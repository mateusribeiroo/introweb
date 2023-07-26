<template>
  <nav class="align-center" aria-label="Page navigation example">
      <ul class="pagination">
        <li class="page-item">
          <a class="page-link" href="#" aria-label="Previous">
            <span aria-hidden="true">&laquo;</span>
          </a>
        </li>
        
        <li
          v-for="i in qtde_pages" :key="i" 
          class="page-item"
          >
          <a class="page-link" href="#">{{ i+1 }}</a>
        </li>

        <li class="page-item">
          <a class="page-link" href="#" aria-label="Next">
            <span aria-hidden="true">&raquo;</span>
          </a>
        </li>
      </ul>
  </nav>
</template>

<script setup>
  import { computed } from 'vue';

  let {total, per_page, page} = defineProps({
    per_page: Number,
    page: Number,
    has_next_page: Boolean
  });

  let qtde_pages = computed(() => total/per_page)
</script>

<style>
  .align-center{
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>