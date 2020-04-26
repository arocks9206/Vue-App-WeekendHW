<template lang="html">
<h2>{{title}}</h2>
</template>

<script>
export default {
  name: "drink-header",
  props: ["title"]
}
</script>

<style lang="css" scoped>
h2 {
  font: bold 30px Cooper Black;
  color: white;
  background-color: #ea5959;
  padding: 5px;
}
</style>
