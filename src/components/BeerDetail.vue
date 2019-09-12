<template>
  <div v-if="beer" class="details">
    <h4>{{beer.name}}</h4>
    <h5>{{beer.tagline}}</h5>
    <p>{{beer.description}}</p>
  </div>
</template>

<script>

export default {
  name: "beer-detail",
  props: ['beer']
}
</script>

<style>

div.details {
  text-align: left;
}

</style>