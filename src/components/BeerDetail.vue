<template>
  <div v-if="beer" class="details">
    <h4>{{beer.name}}</h4>
    <h5>{{beer.tagline}}</h5>
    <p>{{beer.description}}</p>

    <h5>Ingredients:</h5>

    <p v-for="ingredient in beer.ingredients">
      <ul v-for="item in ingredient">
        <li>{{item.name}}</li>
      </ul>
    </p>


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