<template>
<div id='ingredients' class='col'>
    <ul>
        <li v-for="ingr in ingredients">{{ ingr.name }}</li>
    </ul>
</div>
</template>

<script>
var json = require('../assets/food.json');

export default {
  name: 'ingredients',
  data() {
    return {
      ingredients: json
    }
  }
}
</script>

<style lang="stylus">
#ingredients
    background-color lightgreen
    flex 0 0 30%
</style>
