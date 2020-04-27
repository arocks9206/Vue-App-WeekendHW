<template lang="html">
  <div id="app">
    <drink-header title="Juice Joint"/>

    <div id="list-info" v-if="drinks.length">
      <h2>Drinks List</h2>
      <drink-list :drinks="drinks"></drink-list>
      <drink-detail v-if='selectedDrink' :drink='selectedDrink'></drink-detail>
      <button v-on:click='addFavorite'>Add Favorite</button>
    </div>

      <div id="favorite-drinks-list">
        <h2>Favorite Drinks</h2>
        <drink-list :drinks="favoriteDrinks"></drink-list>
        <li v-for="(favoriteDrinks, index) in favoriteDrinks"</li>
        <button v-on:click="removeFavorite(index)">Delete Favorite</button>
      </div>
  </div>
</template>

<script>
import {eventBus} from './main.js';
import DrinkHeader from './components/DrinkHeader.vue';
import DrinkList from './components/DrinkList.vue';
import DrinkDetail from './components/DrinkDetail.vue';

export default {
  name: 'app',

  components: {
    'drink-list': DrinkList,
    'drink-detail': DrinkDetail,
    'drink-header': DrinkHeader
  },

  data() {
    return {
      drinks: [],
      selectedDrink: null,
      favoriteDrinks: []
    }
  },

  mounted (){
    fetch('https://www.thecocktaildb.com/api/json/v1/1/search.php?s')
    .then(result => result.json())
    .then(drinks => this.drinks= drinks.drinks)

    eventBus.$on('drink-selected', (drink) => {
      this.selectedDrink = drink
    })
  },

  methods: {
      addFavorite: function() {
        if (this.favoriteDrinks.includes(this.selectedDrink) === false) {
          this.favoriteDrinks.push(this.selectedDrink);
        }
      },
      removeFavorite: function(index) {
        this.favoriteDrinks.splice(index, 1)
      }
    }
};
</script>

<style lang="css" scoped>
#app {
  max-width: 1200px;
  padding: 20px;
  border-style: ridge;
  border-color: white;
  border-width: 10px;
  background-color: #ffdfd3;
}

h2 {
   font-family: 'Cooper Black', serif;
   color: white;
 }

 #list-info {
    display: flex;
    flex-direction: column;
    padding: 20px;
    align-items: left;
    border-radius: 25px;
    border: 2px solid #e8d5b7;
    background-color: #f98b60;
    padding-top: 40px;
    max-width: 800px;
    font-family: 'Century Gothic', sans-serif;
    color: white;
    font-weight: 400;
    font-size: 18px;
  }

 #favorite-drinks-list {
   display: flex;
   flex-direction: column;
   padding: 20px;
   align-items: left;
   border-radius: 25px;
   border: 2px solid #e8d5b7;
   background-color: #ffc057;
   padding-top: 40px;
   max-width: 800px;
   font-family: 'Century Gothic', sans-serif;
   color: white;
   font-weight: 400;
   font-size: 18px;
 }

 .drink-detail {
   display: flex;
   flex-direction: column;
   padding: 20px;
   align-items: left;
   border-radius: 25px;
   border: 2px solid #e8d5b7;
   background-color: #ea5959;
   padding-top: 40px;
   max-width: 800px;
   font-family: 'Century Gothic', sans-serif;
   color: white;
   font-weight: 400;
   font-size: 18px;
 }

 button {
  font: bold 11px Century Gothic;
  text-decoration: none;
  background-color: #EEEEEE;
  color: #333333;
  padding: 2px 6px 2px 6px;
  border-top: 1px solid #CCCCCC;
  border-right: 1px solid #333333;
  border-bottom: 1px solid #333333;
  border-left: 1px solid #CCCCCC;
}
</style>
