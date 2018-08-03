<template>
<div id='ingredients' class='col col-l'>
  <input value="search" class='search'> <!-- FIXME/TODO (search/filter/autocomplete?) -->

  <ul class='ingr-list'>
    <li v-for="ingr in ingredients">
      <button v-on:click="add(ingr, -1)" class='btn btn-min'>-</button
      <span class='ingr'>{{ ingr.name }}</span>
      <span class='counter'>{{ ingr.amt }}</span>
      <button v-on:click="add(ingr)" class='btn btn-pls'>+</button>
      <!-- TODO when clicking +/-, push number of ingr up to App.vue -->
    </li>
  </ul>
</div>
</template>

<script>
var food = require('../assets/food.json');
// set the initial amount of every ingredient to zero
food.map(function(f) { f.amt = 0; });
console.log(JSON.parse(JSON.stringify(food)));

export default {
  name: 'ingredients',
  data() {
    return {
      ingredients: food
    }
  },
  methods: {
    add: function(ingr, mult=1) {
      // 'add' only if going up or if there's room to go down
      if (mult>=0 || ingr.amt>0) {
        ingr.amt += mult;
      }
    }
  }
}
</script>

<style lang="stylus">
.col-l
    background-color lightgreen
    flex 0 0 30%

.search
    width 100%

.ingr-list
    padding 0
    margin 0
    list-style none
.btn-pls    // button +
    float right
</style>
