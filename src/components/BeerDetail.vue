<template>
  <div v-if='beer'>
    <h2>{{ beer.name }}</h2>
    <p>{{ beer.tagline }}</p>
    <p>{{ beer.description }}</p>
    <p>{{ beer.first_brewed }}</p>
    <button v-if="!favBeers.includes(beer)" v-on:click="addToFavourites">Favourite</button>
  </div>
</template>

<script>
import { eventBus } from '../main.js';
export default {
    name: 'beer-detail',
    props: ['beer', 'favBeers'],
    methods: {
        addToFavourites: function(){
          eventBus.$emit( 'favourited-beer', this.beer )
    }
  }
}
</script>

<style scoped >

</style>