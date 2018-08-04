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
  data() {
    return {
      // get flat list of recipe names
      r_names: this.recipes.map(r => r.name)
    }
  },
  methods: {
    // TODO: find recipes that are *almost* craftable (one/two ingredients off)
    // FIXME: if need ingredient twice, once in dependency, only checks once
    //    e.g. cheeseburger needs tomato and relish (which needs tomato); but if
    //         you just have one tomato it still returns true
    have_ingredients: function(recipe) {
      var have = true;
      for (name in recipe.ingredients) {
        console.log('-', name);
        if (!this.r_names.includes(name)) {
          // ingredient is produce or meat: check ingredient list
          have = have && (this.ingredients[name] >= recipe.ingredients[name]);
        } else {
          // ingredient is a recipe: check ingredient list; if enough, do nothing
          if (this.ingredients[name] < recipe.ingredients[name]) {
            // otherwise get recipe and check recursively
            var next_recipe = this.recipes.filter(function(r) {
              return r.name == name;
            })[0];
            have = have && this.have_ingredients(r);
          }
        }
      }
      // return result
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
