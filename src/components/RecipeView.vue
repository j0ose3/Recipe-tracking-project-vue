<template>
  <tr v-for="recipe in recipes" :key="recipe.name">
    <td>{{ recipe.name }}</td>
    <td>{{ recipe.cuisine }}</td>
    <td><img :alt="recipe.photo" :src="recipe.photo" /></td>
    <td class="content_td">
      <p>{{ recipe.ingredients }}</p>
    </td>
    <td class="content_td">
      <p>{{ recipe.preparation }}</p>
    </td>
    <td>
      <button @click="deleteRecipe(recipe)" name="delete">Delete</button>
    </td>
  </tr>
</template>

<script setup lang="ts">
import type { RecipesType } from '@/types'

defineProps<{ recipes: RecipesType[] }>()
const emit = defineEmits(['delete'])

const deleteRecipe = (recipe: RecipesType) => {
  emit('delete', recipe)
}
</script>

<style scoped></style>
