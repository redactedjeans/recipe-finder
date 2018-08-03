<template>
<div id="app">
    <in-list></in-list>
    <div id="results">
        <ingredients></ingredients>
        <recipes></recipes>
    </div>
</div>
</template>

<script>
import InList from './components/InList.vue'
import Ingredients from './components/Ingredients.vue'
import Recipes from './components/Recipes.vue'

export default {
  name: 'app',
  components: {
    InList,
    Ingredients,
    Recipes,
  }
}
</script>

<style lang="stylus">
// typefaces
// TODO: move this to universal rules (w colours)
// @import url('https://fonts.googleapis.com/css?family=Cutive+Mono|Roboto:100')

// FIXME
*
    box-sizing border-box

// reset
body
  margin 0
 // app
 #results
     background-color pink
     div
         display inline-block
</style>
