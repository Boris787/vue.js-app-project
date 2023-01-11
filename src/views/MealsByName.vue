<template>
  <div class="p-7 ">
    <input 
      type="text"
      v-model="keyword"
      class="rounded border-2 order-gray-200 w-full" 
      placeholder="Search for Meals"
      @change="searchMeals"
      >
      <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-7">
        <div v-for="meal of meals" :key="meal.idMeal" class="bg-white shadow rounded-xl">
          <router-link to="/">
            <img 
              :src="meal.strMealThumb" 
              :alt="strMeal" 
              class="rounded-t-xl w-full h-48 object-cover" 
            />
          </router-link>
          <div class="p-3">
            <h3 class="font-semibold">{{ meal.strMeal }}</h3>
            <p class="mb-4">Lorem ipsum dolor sit amet consectetur adipisicing elit. Perspiciatis voluptatem ad unde illo quaerat enim dolorum.</p>
            <div class="flex items-center justify-between">
              <a :href="meal.strYoutube" target="_blank" class="px-3 py-2 rounded border-2 border-red-600 
                bg-red-500 hover:bg-red-600 transition-colors text-white">
                YouTube
              </a>
              <router-link to="/" class="px-3 py-2 rounded border-2 border-blue-600 
                bg-blue-500 hover:bg-blue-600 transition-colors text-white">
                View
              </router-link>
          </div>
          </div>
        </div>
      </div>
    </div> 
</template>

<script setup>
import { computed, onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';

const route = useRoute();
const keyword = ref('');
const meals = computed(() => store.state.searchedMeals)

function searchMeals() {
  store.dispatch('searchMeals', keyword.value)
}

onMounted(() => {
  keyword.value = route.params.name
  if (keyword.value) {
    searchMeals()
  }
})

</script>
