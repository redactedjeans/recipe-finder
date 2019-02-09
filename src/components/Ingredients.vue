<template>
<div id='ingredients' class='col col-l'>
  <input placeholder='search' class='search'> <!-- FIXME/TODO (search/filter/autocomplete?) -->
  <button v-on:click="reset" class='btn'>Reset</button>

  <ul class='ingredient-list'>
    <li v-for="(amt, name) in ingredients" :key="name" class='ingredient'>
      <button v-on:click="add(name, -1)" class='btn btn-min'>-</button>
      <span class='ingredient'>{{ name }}</span>
      <span class='counter'>{{ amt }}</span>
      <button v-on:click="add(name)" class='btn btn-pls'>+</button>
    </li>
  </ul>
</div>
</template>

<script>
export default {
  name: 'ingredients',
  props: {
    ingredients: Object
  },
  methods: {
    add: function(name, mult=1) {
      // 'add' only if going up or if there's room to go down
      if (mult>=0 || this.ingredients[name]>0) {
        this.ingredients[name] += mult;
        //
      }
    },
    reset: function() {
      for (name in this.ingredients) {
        this.ingredients[name] = 0;
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
