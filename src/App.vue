<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HeaderBar from './components/HeaderBar.vue';
</script>

<template>
  <header>
    <link rel="stylesheet" href="node_modules/bootstrap/dist/css/bootstrap.css">
    <div class="wrapper">
      
    </div>
  </header>
  <HeaderBar />


  <RouterView />
</template>

<style scoped>

</style>
