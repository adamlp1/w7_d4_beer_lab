<template>
<div>
    <h1>Favourite Beers</h1>
   <ul>
   <li v-for="(favBeer, index) in favBeers" :favBeer="favBeer" :key="index">{{favBeer.name}} <button v-on:click="removeFromFavourite" >remove</button> </li>
   </ul>
   </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
    name: 'favourited-beer',
    props: ['favBeers'],
    methods: {
      removeFromFavourite: function(){
        eventBus.$emit( 'remove-beer', favBeer)
      }
    }
}
</script>

<style>

</style>