<template lang="html">
  <div>
    <h3>{{drink.strDrink}}</h3>
    <img :src="drink.strDrinkThumb" width='80' height= '70'>
    <h4>Instructions</h4>
    <p>{{drink.strInstructions}}</p>
    <h4>Ingredients</h4>
    <p>{{drink.strIngredient1}}</p>
    <p>{{drink.strIngredient2}}</p>
    <p>{{drink.strIngredient3}}</p>
  </div>
</template>

<script>
export default {
  name: 'drink-detail',
  props: ['drink']
}
</script>

<style lang="css" scoped>
h3 {
    font-family: 'Cooper Black', serif;
    color: white;
    font-weight: 900;
    font-size: 24px;
}

h4 {
  font-family: 'Cooper Black', serif;
  color: white;
  font-weight: 800;
  font-size: 20px;
}

p {
   font-family: 'Century Gothic', sans-serif;
   color: white;
   font-weight: 200;
   font-size: 18px;
 }
</style>
