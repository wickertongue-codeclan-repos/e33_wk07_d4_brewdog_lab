<template>
  
  <div id="beer-list">
    <beer-item v-for="(beer, index) in beers" :beer="beer" :key="index"></beer-item>
  </div>

</template>

<script>
import BeerItem from './BeerItem'

export default {
  name: 'beer-list',
  props: ['beers'],
  components: {
    'beer-item': BeerItem
  }
}

</script>

<style>

#beer-list {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

</style>