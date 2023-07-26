<script setup>
  import AnimeCard from './AnimeCard.vue';
  import api from '../services/api';
  import { computed, onMounted, ref } from 'vue';

  let anime_list = ref([]); 
  let searchAnimeField = ref("");
  let qtde_pages, has_next_page, page, per_page_var;
  
  async function fetchAnimes(page, per_page){ 
    await api.get(`/anime?limit=${per_page}&order_by=rank&page=${page}`).then((response) => {
      anime_list.value = response.data.data;
      has_next_page = response.data.pagination;
      qtde_pages = response.data.pagination.items.per_page/5;
      per_page_var = response.data.pagination.items.per_page;
    });
  }
  
  onMounted(fetchAnimes(page | 1, per_page_var | 25));
  
  const filteredAnimes = computed(() => {
    if(anime_list.value && searchAnimeField.value){
      return anime_list.value.filter(anime => anime.title.toLowerCase().includes(searchAnimeField.value.toLowerCase()))
    }
    return anime_list.value
  })

  function animeNextPage(page, per_page_var){
    return fetchAnimes(page | 1, per_page_var | 25);
  }

  
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


  <nav class="align-center" aria-label="Page navigation example">
      <ul class="pagination">
        <li class="page-item">
          <a class="page-link" href="#" aria-label="Previous">
            <span aria-hidden="true">&laquo;</span>
          </a>
        </li>
        
        <li
          v-for="i in qtde_pages" :key="i" 
          class="page-item"
          >
          <a :on-click="animeNextPage(i, 25)" class="page-link" href="#">{{ i }}</a>
        </li>

        <li v-if="has_next_page" class="page-item">
          <a class="page-link" href="#" aria-label="Next">
            <span aria-hidden="true">&raquo;</span>
          </a>
        </li>
      </ul>
  </nav>

</template>

<style>
  .align-center{
      display: flex;
      align-items: center;
      justify-content: center;
  }
</style>
