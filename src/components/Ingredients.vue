<template>
<div id='ingredients'>
    <ul>
        <li v-for="ing in ingredients">{{ ing }}</li>
    </ul>
</div>
</template>

<script>
export default {
  name: 'ingredients',
  data() {
    return {
      ingredients: []
    }
  }
}
</script>

<style lang="stylus">
#ingredients
    background-color lightgreen
    width 200px
</style>
