<script setup>
import { useRoute } from 'vue-router';
import { onMounted, onUpdated} from 'vue';
import api from '../services/api';

const route = useRoute();

let mal_id = route.params.id;
let anime = {};

const fetchAnime = async () => {
   
    await api.get(`/anime/${mal_id}`).then((response) => {
        anime = response.data.data;
        console.log(anime)
    });

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
        <h4>Eps: {{ anime.episodes }}</h4>
        <h4>Nota: {{ anime.score }}</h4>
    </div>
   

</template>



<style>

</style>