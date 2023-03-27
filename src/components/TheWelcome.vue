<script setup>
  import AnimeCard from './AnimeCard.vue';
  import api from '../services/api';
  import { computed, onMounted, ref } from 'vue';

  let anime_list = ref([]);
   
  const fetchAnimes = async () => api.get("/anime?limit=20").then((response) => {
    anime_list.value = response.data.data;
    console.log(anime_list.value);
  });

  onMounted(fetchAnimes);
    
</script>

<template>
  <div class="row row-cols-1 row-cols-md-3 g-4">
    <AnimeCard 
      v-for="(item, index) in anime_list" :key="index"
      :title="item.title"
      :synopsis="item.synopsis"
      :jpg_image_url="item.images.jpg.image_url"
    />
  </div>
</template>
