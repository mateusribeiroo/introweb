<script setup>
import { useRoute } from 'vue-router';
import { onBeforeMount, onMounted } from 'vue';
import api from '../services/api';

const route = useRoute();

let mal_id = route.params.id;
let anime = {};

const fetchAnime = async () => {
   
    await api.get(`/anime/${mal_id}`).then((response) => {
        anime = response.data.data;
        console.log(anime)
    })

}

onMounted(fetchAnime);

</script>

<template>

    <div id="principal">
        <img src="" alt="">
        <h2>{{ anime.title }}</h2>
    </div>

    <div>
        {{ anime.synopsis }}
    </div>

    <div>
        Eps: {{ anime.episodes }}
        Nota: {{ anime.score }}
    </div>

</template>



<style>

</style>