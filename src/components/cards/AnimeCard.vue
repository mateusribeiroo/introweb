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
        <div class="card" v-for="(item, index) in anime_list" :key="item.mal_id">
            <h2 class="title">{{ index+1 }} {{ item.title }}</h2>
        </div>
    </div>

</template>

<style scoped>
    .card{
        background-color: grey;
        width: 10vw;
        height: 10vh;

        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: center;
        padding: auto;

        margin: 2rem;
    }

    .place{
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: center;
        align-content: space-between;
    }

    .title{
        font-size: 1rem;
        color: black;
    }
</style>