<script>
    import api from "../../services/api";
    import { onMounted, ref, computed } from "vue"
    
    let search_anime_field = ref("");
    let anime_list = ref(); 

    const animes_filtered = computed(() => {

    })    


    export default({
        name: "AnimeCard",
        setup() {

            const fetchAnimes = async () => api.get("/anime?limit=20").then((response) => {
                anime_list.value = response.data.data;
                console.log(anime_list.value);
            });

            onMounted(fetchAnimes);
            return { anime_list }
        },

       
    })

</script>

<template>
    <div class="row row-cols-1 row-cols-md-3 g-4"  >
        <div class="col" v-for="item in anime_list" :key="item.mal_id">
            <div class="card">
            <img :src=item.images.jpg.image_url class="card-img-top" alt="...">
            <div class="card-body">
                <h5 class="card-title">{{ item.title }}</h5>
                <p class="card-text">{{ item.synopsis }}</p>
            </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .place{
        
        width: 100vw;
    }

    .anime_card{
        width: 25%;
        height: 10%;
        margin: 2% 1%;
    }
</style>