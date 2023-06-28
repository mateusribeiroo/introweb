<template>
    <nav class="bg-dark navbar navbar-expand-lg bg-body-tertiary" data-bs-theme="dark">
        <div class="container-fluid">
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarTogglerDemo01" aria-controls="navbarTogglerDemo01" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarTogglerDemo01">
            <router-link class="navbar-brand" to="#">Encontre seu anime</router-link>
            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
              <li class="nav-item">
                <router-link class="nav-link active" to="/" >INÍCIO</router-link>
              </li>
              <li class="nav-item">
                <router-link class="nav-link" to="/about">Sobre Este Projeto</router-link>
              </li>
            </ul>
          </div>
        </div>
      </nav>
</template>

<script setup>

</script>

<style>

</style>