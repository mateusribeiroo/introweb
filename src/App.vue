<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HeaderBar from './components/HeaderBar.vue';
import FooterBar from './components/FooterBar.vue';
</script>

<template>
  <link rel="stylesheet" href="node_modules/bootstrap/dist/css/bootstrap.css">
  <HeaderBar />

  <RouterView />
  
  <FooterBar />
</template>

<style scoped>

</style>
