<template>
<div>
  <div class="p-7 pb-0 ">
    <input 
      type="text"
      v-model="keyword"
      class="rounded border-2 bg-white order-gray-200 focus:ring-orange-500 focus:border-orange-500" 
      placeholder="Search for Meals"
      @change="searchMeals"
      >
    </div> 
    <Meals :meals="meals" />
</div>
</template>

<script setup>
import { computed, onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store'
import YouTubeButton from '../components/YouTubeButton.vue';
import MealItem from '../components/MealItem.vue'
import Meals from '../components/Meals.vue'


const route = useRoute();
const keyword = ref('');
const meals = computed(() => store.state.searchedMeals)

function searchMeals() {
  if(keyword.value) {
    store.dispatch('searchMeals', keyword.value)
  } else {
    store.commit('setSearchedMeals', [])
  }
}

onMounted(() => {
  keyword.value = route.params.name
  if (keyword.value) {
    searchMeals()
  }
})

</script>
