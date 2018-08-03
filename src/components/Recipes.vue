<template>
<div id='recipes' class='col col-r'>
  <ul class='recipe-list'>
    <li v-for="recipe in recipes" v-if="have_ingredients(recipe)">{{ recipe.name }}</li>
  </ul>
</div>
</template>

<script>

export default {
  name: 'recipes',
  props: {
    ingredients: Object,
    recipes: Array
  },
  methods: {
    have_ingredients: function(recipe) {
      var have = true;
      // var ingredients = this.ingredients;
      for (name in recipe.ingredients) {
        if (this.ingredients[name] < recipe.ingredients[name]) {
          have = false;
        }
      }
      return have;
    }
  }
}
</script>

<style lang="stylus">
.col-r
    background-color lightblue
    flex 1
</style>
