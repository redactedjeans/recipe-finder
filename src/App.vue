<template>
<div id="app" class='container'>
    <ingredients></ingredients>
    <recipes></recipes>
</div>
</template>

<script>
import Ingredients from './components/Ingredients.vue'
import Recipes from './components/Recipes.vue'

export default {
  name: 'app',
  components: {
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
.container
    background-color pink
    display flex

.col
    padding 10px
</style>
