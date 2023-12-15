<script setup lang="ts">
import { ref } from 'vue'

import RecipeCreate from './components/RecipeCreate.vue'
import RecipeList from './components/RecipeList.vue'
import RecipeData from './RecipeData.js'
import type { RecipesType } from './types'

const recipes = ref<RecipesType[]>(RecipeData)

const createRecipe = (recipe: RecipesType) => {
  recipes.value.push(recipe);
}


const deleteRecipe = (recipeToDelete: RecipesType) => {
  // Find the index of the recipe to delete
  const index = recipes.value.findIndex((recipe) => recipe === recipeToDelete);

  // If found, remove the recipe from the array
  if (index !== -1) {
    recipes.value.splice(index, 1);
  }
};

</script>


<template>
  <div class="App">
    <header>
      <h1>Delicious Food Recipes</h1>
    </header>
    <RecipeList :recipes="recipes" @delete="deleteRecipe" />
    <RecipeCreate @create-recipe="createRecipe" />
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css?family=Open+Sans|Playfair+Display+SC');

.App {
  padding: 1em;
}

label {
  display: inline-block;
  width: 100px;
}

header {
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
}

h1 {
  font:
    64px 'Playfair Display SC',
    serif;
  text-align: center;
}

img {
  width: 100px;
  height: 100px;
  object-fit: scale-down;
}

/* zebra striping */

tbody tr:nth-child(odd) {
  background-color: #fff0c7;
}

/* typography */

html {
  font-family: 'helvetica neue', sans-serif;
}

thead th,
tfoot th {
  font-family: 'Rock Salt';
}

th {
  letter-spacing: 2px;
  padding: 10px;
}

td {
  letter-spacing: 1px;
  overflow-x: hidden;
  overflow-y: hidden;
  font-size: 12px;
  padding: 10px;
  text-align: center;
}

/* spacing */

table {
  table-layout: fixed;
  width: 100%;
  border-collapse: collapse;
  overflow: hidden;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
}

.content_td p {
  max-width: 100%;
  max-height: 100px;
  overflow-y: auto;
  text-overflow: ellipsis;
}

/* Column Size for thead */

thead th:nth-child(1) {
  width: 10%;
}

thead th:nth-child(2) {
  width: 10%;
}

thead th:nth-child(3) {
  width: 10%;
}

thead th:nth-child(4) {
  width: 30%;
}

thead th:nth-child(5) {
  width: 30%;
}

thead th:nth-child(6) {
  width: 10%;
}

/* Column size for tbody */

tbody td:nth-child(1) {
  width: 10%;
}

tbody td:nth-child(2) {
  width: 10%;
}

tbody td:nth-child(3) {
  width: 10%;
}

tbody td:nth-child(4) {
  width: 30%;
}

tbody td:nth-child(5) {
  width: 30%;
}

tbody td:nth-child(6) {
  width: 10%;
}
</style>
