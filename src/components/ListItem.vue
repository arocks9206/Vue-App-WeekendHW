<template lang="html">
  <div>
    <li v-on:click="handleClick">{{drink.strDrink}}</li>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'list-item',
  props: ['drink'],
  methods: {
    handleClick() {
      eventBus.$emit('drink-selected', this.drink)
    }
  }
}
</script>

<style lang="css" scoped>


</style>
