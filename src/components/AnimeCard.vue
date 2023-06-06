<script setup>
    const stringLimit = 50;
    
    let props = defineProps(['title', 'synopsis', 'jpg_image_url'])

    function readMoreandLess(e){
        console.log(e)
        if(e.target.innerText == "Ler mais..."){
            e.target.innerText = "Ler menos";
            e.target.parentElement.children[1].hidden = true
            e.target.parentElement.children[2].hidden = false;
        }else{
            e.target.innerText = "Ler mais..."
            e.target.parentElement.children[1].hidden = false
            e.target.parentElement.children[2].hidden = true;
        }
    }

</script>

<template>
    <div class="col">
        <div class="card anime_card">
            <img :src=jpg_image_url class="card-img-top" alt="...">
            <div class="card-body">
                <h5 class="card-title">{{ title }}</h5>
                <p class="card-text ">{{ synopsis.substring(0, stringLimit)}}</p>
                <p hidden class="card-text ">{{synopsis}}</p>
                <a href="#" v-on:click="readMoreandLess($event)">Ler mais...</a>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .place{
        width: 100vw;
    }

    .anime_card{
        width: 20vw;
        height: 10%;
        margin: auto;
    }
</style>