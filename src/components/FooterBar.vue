<template>
    <footer class="footer"> 
        <div class="copyright">
            <p>&#169; Todos os direitos reservados</p>
        </div>

        <div class="">
            <p></p>
        </div>

        <div class="luffyContainer">
            <img class="luffy rounded" src="https://i.pinimg.com/736x/e5/06/3a/e5063ab4702dfe442e0f7be9379d532e.jpg" alt="Luffy flamenguista">
        </div>
    </footer>
</template>

<script setup>

</script>

<style>
    .footer{
        background-color: black;

        display: flex;
        align-items: center;
        justify-content: space-between;

        max-height: fit-content;
    }

    .copyright{
        margin-left: 10%;
    }

    .luffyContainer{
        width: 30%; 
        margin: auto 0;
    }

    .luffy{
        max-width: 50%;
        margin: 10% 0;
        object-fit: cover;
    }
</style>