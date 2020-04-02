<template>
<div>
 <h2>Beer List:</h2>
 <ul>
   <beer-selected v-for="(beer, index) in beers" :beer="beer" :key="index">{{beer.name}}</beer-selected>
   </ul>
</div>
</template>

<script>
import BeerSelected from './BeerSelected.vue';

export default {
  name: 'beer-list',
  props: ['beers'],
  components: {
    "beer-selected": BeerSelected
  }
}
</script>

<style scoped>

</style>