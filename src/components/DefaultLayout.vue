<template>
    <div class="bg-gray-200 h-max">
      <Navbar />
    <main>
      <router-view />
    </main>
  </div>
</template>

<script setup>
import Navbar from '../components/Navbar.vue'

</script>
