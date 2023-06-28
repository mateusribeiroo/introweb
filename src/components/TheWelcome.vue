<script setup>
  import AnimeCard from './AnimeCard.vue';
  import api from '../services/api';
  import { ref } from 'vue';

  let anime_list = ref([]); 
  let searchAnimeField = ref("");

  const handleSearch = async () =>{
    anime_list.value = await api.get(`/anime?q=${searchAnimeField.value}&limit=25`)
      .then(data => data.data.data)
  }

</script>

<template>   

  <form class="mb-3"  @submit.prevent="handleSearch">
    <label for="searchAnimeField" hidden class="form-label"></label>
    <input placeholder="Pesquisar..." class="form-control" type="search" v-model="searchAnimeField" >
  </form>

  <div class="row row-cols-1 row-cols-md-3 g-4">
    <AnimeCard 
      v-for="(item, index) in anime_list" :key="index"
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
