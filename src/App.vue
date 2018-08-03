<template>
<div id="app" class='container'>
    <ingredients :ingredients="ingredients"></ingredients>
    <recipes :recipes="recipes" :ingredients="ingredients"></recipes>
</div>
</template>

<script>
import Ingredients from './components/Ingredients.vue'
import Recipes from './components/Recipes.vue'

// get all recipes
var recipes = require('./assets/food.json');
// parse recipe list to create ingredient list
var ingredients = [];
recipes.forEach(function(recipe) {
  recipe.ingredients.forEach(function(ingredient) {
    if (!ingredients.includes(ingredient)) {  // FIXME!!!
      ingredients.push({"name": ingredient.name, "amt":0});
    }
  });
});
// console.log(JSON.parse(JSON.stringify(ingredients)));

export default {
  name: 'app',
  components: {
    Ingredients,
    Recipes,
  },
  data() {
    return {
      recipes: recipes,
      ingredients: ingredients
    }
  }
}
</script>

<style lang="stylus">
// typefaces
// TODO: move this to universal rules (w colours)
// @import url('https://fonts.googleapis.com/css?family=Cutive+Mono|Roboto:100')

// FIXME
// reset
*
    box-sizing border-box
body
    margin 0

// app
.container
    background-color pink
    display flex
.col
    padding 10px
</style>
