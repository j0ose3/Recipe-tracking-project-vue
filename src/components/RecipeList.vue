<template>
  <div className="recipe-list">
    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>Cuisine</th>
          <th>Photo</th>
          <th>Ingredients</th>
          <th>Preparation</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody v-if="recipes">
        <RecipeView :recipes="recipes" @delete="deleteRecipe" />
      </tbody>
    </table>
  </div>
</template>

<script setup lang="ts">
import RecipeView from './RecipeView.vue';
import type { RecipesType } from '@/types'

defineProps<{
  recipes: RecipesType[]
}>()

const emit = defineEmits(['delete']);

const deleteRecipe = (recipe: RecipesType) => {
    emit('delete', recipe);
}


</script>

<style scoped></style>
