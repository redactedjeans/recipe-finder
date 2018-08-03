<template>
<div id='list'>
    <select id="in-list">
        <option value="">--Select an ingredient--</option>
        <option v-for="ing in ingredients">{{ ing.name }}</option>
    </select>

    <input type="number"> <!-- number in inventory --> </input>

    <button>Add</button> <!-- TODO: onclick, send ingredient+num back up to app -->
</div>
</template>

<script>
var json = require('../assets/food.json');
console.log(JSON.parse(JSON.stringify(json)));

export default {
  name: 'in-list',
  data() {
    return {
      ingredients: json
    }
  }
}
</script>

<style lang="stylus">
</style>
