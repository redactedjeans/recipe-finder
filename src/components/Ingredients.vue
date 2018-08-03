<template>
<div id='ingredients' class='col col-l'>
  <input value="search" class='search'> <!-- FIXME/TODO (search/filter/autocomplete?) -->

  <ul class='ingredient-list'>
    <li v-for="ingredient in ingredients" class='ingredient'>
      <button v-on:click="add(ingredient, -1)" class='btn btn-min'>-</button
      <span class='ingredient'>{{ ingredient.name }}</span>
      <span class='counter'>{{ ingredient.amt }}</span>
      <button v-on:click="add(ingredient)" class='btn btn-pls'>+</button>
      <!-- TODO when clicking +/-, push number of ingr up to App.vue -->
    </li>
  </ul>
</div>
</template>

<script>
export default {
  name: 'ingredients',
  props: {
    ingredients: Array
  },
  methods: {
    add: function(ingredient, mult=1) {
      // 'add' only if going up or if there's room to go down
      if (mult>=0 || ingredient.amt>0) {
        ingredient.amt += mult;
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

.ingredient-list
    padding 0
    margin 0
    list-style none
.btn-pls    // button +
    float right
</style>
