<template>
  <div class="flex flex-col p-8">
    <div class="items-center justify-center">
    </div>
  </div>
</template>

<script setup>
import { computed, onMounted, ref } from "vue";
import store from "../store"
import axiosClient from '../axiosClient.js'


const ingredients = ref([])

onMounted(async () => {
  const response = await axiosClient.get('/list.php?i=list')
  ingredients.value = response.data
})
</script>
