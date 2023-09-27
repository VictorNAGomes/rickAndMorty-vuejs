<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="header">
      <h1 class="title">Rick and Morty</h1>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
  template {
    display: flex;
  }

  .title {
    font-size: 50px;
  }
</style>
