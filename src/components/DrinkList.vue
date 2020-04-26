<template lang="html">
  <div>
    <ul>
      <list-item v-for="(drink, index) in drinks" :drink="drink" :key="index"></list-item>
    </ul>
  </div>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
  name: 'drink-list',
  props: ['drinks'],
  components: {
    'list-item': ListItem
  }
}
</script>

<style lang="css" scoped>
#list-item {
    list-style-type: rectangle;
    padding: 5px;
}
</style>
