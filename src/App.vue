<template>
  <div>
    <beer-list :beers='beers'></beer-list>
    <beer-detail :beer='selectedBeer' :favBeers='favouriteBeer'></beer-detail>
    <favourited-beer :favBeers='favouriteBeer'></favourited-beer>
  </div>
</template>
 
<script>

import FavouritedBeer from './components/FavouritedBeer'
import BeerList from './components/BeerList.vue'
import BeerDetail from './components/BeerDetail.vue'
import { eventBus } from './main'

export default {
  data(){
    return {
      beers: [],
      favouriteBeer: [],
      selectedBeer: null
    }
  },
  components: {
    'beer-list': BeerList,
    'beer-detail': BeerDetail,
    'favourited-beer': FavouritedBeer
  

  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beersRes => this.beers = beersRes)

    eventBus.$on( 'beer-selected', (beer) => {
      this.selectedBeer = beer;
    })

    eventBus.$on ('favourited-beer', (beer)=> {
      this.favouriteBeer.push(beer);
    })

    eventBus.$on ('remove-beer', (favBeer)=> {
      const index = this.favouriteBeer.indexOf(favBeer)
      console.log(favBeer);
      
      console.log(index);
      
      this.favouriteBeer.remove(favBeer)
    })
  }
}
</script>

<style scoped>
h1 {
  color: red;
}
</style>
