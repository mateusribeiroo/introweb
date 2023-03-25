<script>
    import api from "../../services/api";
    import { onMounted, ref,  } from "vue"

    export default({
        name: "AnimeCard",
        setup() {
            let anime_list = ref([]);

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
    <div class="place">
        <div class="anime_card card text-bg-dark" v-for="(item, index) in anime_list" :key="item.mal_id">
            <img  :src=item.images.jpg.image_url class="card-img" alt="...">

            <div class="card-img-overlay">
                <h5 class="card-title">{{ index }}: {{ item.title }}</h5>
                <p class="card-text">{{ item.synopsis }}</p>
                <p class="card-text"><small>{{ item.rank }}</small></p>
            </div>>
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