<template>
  <div class="main-app">
    <h1>Brewdog Beers!</h1>
    <h2>Favourite Beers</h2>
    <div class="upper-part-of-page">
      <div id="favourite-beers" class="scroll">
        <ul>
          <li v-for="beer in favouriteBeers">{{beer.name}}</li>
        </ul>
      </div>

      <div class="beer-details">
        <beer-detail :beer = "selectedBeer"></beer-detail>
      </div>

    </div>
      <beer-list :beers="beers"></beer-list>
    
  </div>

</template>

<script>
import BeerList from './components/BeerList'
import BeerDetail from './components/BeerDetail'
import { eventBus } from './main';

export default {
  data() {
    return {
      beers: [],
      favouriteBeers: [],
      selectedBeer: null
    }
  },
  mounted() {
    fetch('https://api.punkapi.com/v2/beers')
    .then(response => response.json())
    .then(beers => this.beers = beers)

    eventBus.$on('favourited-beer', (beer) => {
      if (this.favouriteBeers.includes(beer)===false) {
        this.favouriteBeers.push(beer);
      } 
    })

    eventBus.$on('beer', (beer) => {
      this.selectedBeer = beer;
    })
  },
  components: {
    'beer-list': BeerList,
    'beer-detail': BeerDetail
  }
}

</script>

<style>

div.scroll {
  border: 1px solid black;
  width: 48%;
  height: 200px;
  float: left;
  overflow: auto;
  text-align: justify;
  overflow: -moz-scrollbars-vertical; 
  overflow-y: scroll;
}

h2 {
  text-align: left;
}

div.upper-part-of-page {
  display: flex;
  flex-direction: row;
}

div.beer-details {
  padding-left: 5px;
  border: 1px solid black;
  width: 48%;
  height: 200px;
  margin-left: 10px;
  float: right;
  overflow: auto;
  overflow: -moz-scrollbars-vertical; 
  overflow-y: scroll;
}

</style>