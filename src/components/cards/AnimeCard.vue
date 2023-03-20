<script>
    import api from "../../services/api";
    import { defineComponent, onMounted, ref } from "vue"

    export default defineComponent({
        name: "animeCard",
        setup() {
            const animes = ref([]);

            const fetchAnimes = async () => api.get("/anime?limit=20").then((response) => {
                console.log(response)
            });

            onMounted(fetchAnimes);
        }
    })

</script>

<template>
    <div>
        
    </div>
</template>

<style scoped>

</style>