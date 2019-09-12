<template>
  
  <div id="beer" v-bind:style="{ backgroundImage: `url('${beer.image_url}')`}">
    <h3>{{beer.name}}</h3>
    <button v-on:click="handleClick">Add to Favourites</button>
    <button v-on:click="handleClickForDetails">Show Details</button>
  </div>

</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'beer-item', 
  props: ['beer'],
  methods: {
    handleClick () {
      eventBus.$emit('favourited-beer', this.beer)
    },
    handleClickForDetails () {
      eventBus.$emit('beer', this.beer)
    }
  }
}
</script>

<style>

#beer {
  width: 100px;
  height: 400px;
  background-size: 100px;
  background-repeat: no-repeat;
  background-position: center;
  padding: 10px;
  display: flex;
  flex-wrap: nowrap;
  flex-direction: column;
}

h3 {
  align-items: center;
  position: relative;
  text-align: center;
  top: 200px;
  color: white;
  background-color: black;
  border: 1px solid yellow;
}

div {
  text-align: center;
}

button {
  width: 80px;
  background-color: black;
  color: white;
  border: 1px solid yellow;
  position: relative;
  align-self: center;
  justify-self: baseline;
}

</style>