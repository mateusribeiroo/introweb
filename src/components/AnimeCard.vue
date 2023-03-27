<script setup>
    let props = defineProps(['title', 'synopsis', 'jpg_image_url'])
</script>

<template>
    <div class="col">
        <div class="card">
        <img :src=jpg_image_url class="card-img-top" alt="...">
        <div class="card-body">
            <h5 class="card-title">{{ title }}</h5>
            <p class="card-text">{{ synopsis }}</p>
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