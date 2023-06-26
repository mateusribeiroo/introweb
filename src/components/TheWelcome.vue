<script setup>
  import AnimeCard from './AnimeCard.vue';
  import api from '../services/api';
  import { computed, onMounted, ref } from 'vue';

  let anime_list = ref([]); 
  let searchAnimeField = ref("");
  let qtde_pages, has_next_page, page, per_page_var;
  
  const fetchAnimes = async () => { 
    await api.get(`/anime?limit=25&order_by=rank&page=1`).then((response) => {
      anime_list.value = response.data.data;
      has_next_page = response.data.pagination;
      qtde_pages = response.data.pagination.items.per_page/5;
      per_page_var = response.data.pagination.items.per_page;
    });
  }
  
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
      :mal_id="item.mal_id"
    />
  </div>

</template>

<style>
  .align-center{
      display: flex;
      align-items: center;
      justify-content: center;
  }
</style>
