<template>
<div> 
    <div class="p-8 pb-0">
      <h1 class="text-4xl font-bold mb-4 text-orange-500"> Meals by Letter</h1>      
    </div>
    <div class="flex justify-center gap-2 mt-2">
      <router-link 
        :to="{name: 'byLetter', 
        params: {letter}}" 
        v-for="letter of letters" 
        :key="letter"
        class="hover:text-orange-500 transition-colors"
      >
        {{ letter }}
      </router-link>
    </div>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-7">
        <MealItem v-for="meal of meals" :key="meal.idMeal" :meal="meal" />
      </div>
</div>
</template>

<script setup>
import { computed, onMounted, watch } from "@vue/runtime-core";
import { useRoute } from "vue-router";
import store from '../store';
import MealItem from '../components/MealItem.vue'

const route = useRoute();
const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split("");
const meals = computed(() => store.state.mealsByLetter)

watch(route, () => {
  store.dispatch('searchMealsByLetter', route.params.letter)
})

onMounted(() => {
  store.dispatch('searchMealsByLetter', route.params.letter)
})


</script>
