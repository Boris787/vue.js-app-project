<template>
    <div>
      <Navbar />
    <main>
      <div>
        <router-view />
      </div>
    </main>
  </div>
</template>

<script setup>
import Navbar from '../components/Navbar.vue'

</script>
