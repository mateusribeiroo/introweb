<script setup>
  import AnimeCard from './AnimeCard.vue';
  import Pagination  from './Pagination.vue'
  import api from '../services/api';
  import { computed, onMounted, ref } from 'vue';
  import { limitString } from '../util/strings/limitString';
import PaginationVue from './Pagination.vue';

  let anime_list = ref([]); 
  let searchAnimeField = ref("");
  let pagination = {};

  const fetchAnimes = async () => api.get("/anime?limit=50").then((response) => {
    anime_list.value = response.data.data;
    console.log(anime_list.value);
  });

  onMounted(fetchAnimes);
  
  const filteredAnimes = computed(() => {
    if(anime_list.value && searchAnimeField.value){
      return anime_list.value.filter(anime => anime.title.toLowerCase().includes(searchAnimeField.value.toLowerCase()))
    }
    return anime_list.value
  })

</script>

<template>
  <div class="mb-3">
    <label for="searchAnimeField" hidden class="form-label"></label>
    <input placeholder="Pesquisar..." class="form-control" type="text" v-model="searchAnimeField">
  </div>

  <div class="row row-cols-1 row-cols-md-3 g-4">
    <AnimeCard 
      v-for="(item, index) in filteredAnimes" :key="index"
      :title="item.title"
      :synopsis="item.synopsis"
      :jpg_image_url="item.images.jpg.image_url"
    />
  </div>

  <Pagination />
</template>
