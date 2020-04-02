<template>
  <div>
<h3 v-on:click="handleClick"> {{beer.name}}</h3>
<!-- <button  v-on:click="addToFavourites">Favourite</button> -->
  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'beer-selected',
  props: ['beer'],
  methods: {
    handleClick(){
      eventBus.$emit( 'beer-selected', this.beer )
    },
    
  }

}
</script>

<style scoped>

</style>