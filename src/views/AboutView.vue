<template>
  <div class="about">
    <h1>Olá bom dia! Tudo bem?</h1>
    <h4 class="aboutDescription">
      Este é um trabalho de VueJs que busca usar diretivas como v-for v-model e outras funções nativas do framework consumindo uma API externa e mostrando os dados em tela.<br><br>
      O consumo da API foi a JikanAPI que pode ser acessa clicando neste <a href="https://jikan.moe/">link</a>.<br><br>
      Também foi utilizado RouterLink de forma que apenas o conteúdo das páginas fossem carregados. Componentes como footer e header não recarregam.
    </h4>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
  }

  .aboutDescription{
    width: 70%;
    text-align: center;
  }
}
</style>
