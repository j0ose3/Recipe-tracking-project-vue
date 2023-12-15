<template>
  <form name="create" @submit.prevent="handleSubmit" >
    <table>
      <tbody>
        <tr>
          <td>
            <input type="text" id="name" name="Name" v-model="name" placeholder="Name" />
          </td>
          <td>
            <input type="text" id="Cuisine" name="Cuisine" v-model="cuisine" placeholder="Cuisine" />
          </td>
          <td>
            <input type="url" id="Photo" name="Photo" v-model="photo" placeholder="Photo" />
          </td>
          <td>
            <textarea type="text" id="Ingredients" name="Ingredients" v-model="ingredients" placeholder="Ingredients" />
          </td>
          <td>
            <textarea type="text" id="Preparation" name="Preparation" v-model="preparation" placeholder="Preparation" />
          </td>
          <td>
            <button>Create</button>
          </td>
        </tr>
      </tbody>
    </table>
  </form>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const name = ref('');
const cuisine = ref('');
const photo = ref('');
const ingredients = ref('');
const preparation = ref('');

const emit = defineEmits(['create-recipe']);

const handleSubmit = () => {
  let recipe = {
    name: name.value, 
    cuisine: cuisine.value,
    photo: photo.value, 
    ingredients: ingredients.value,
    preparation: preparation.value
  }
  
  emit('create-recipe',recipe); 

  name.value = '';
  cuisine.value = '';
  photo.value = ''; 
  ingredients.value = '';
  preparation.value = '';
}

</script>

<style scoped></style>
