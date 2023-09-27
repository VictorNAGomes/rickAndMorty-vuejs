<script setup lang="ts">
  const character = defineProps(["id", "name", "url", "species", "gender"]);
  let url = "/character/" + character.id
</script>

<template>
  <RouterLink :to="url">
    <div class="card">
      <img
        :src="character.url"
        class="characterImage"
        alt="Imagem Character"
      />
      <h3>{{ character.name }}</h3>
      <p>{{ character.species }}</p>
    </div>
  </RouterLink>
</template>

<style>
  a {
    text-decoration: none;
    color: inherit;
  }

  .card {
    display: flex;
    flex-direction: column;
    align-items: center;
    border: 1px solid black;
    padding: 1rem;
    border-radius: 1rem;
    text-decoration: none;
  }

  .characterImage {
    height: 75px;
    width: 75px;
    border-radius: 50%;
    margin-bottom: 1rem;
  }

  .card h3 {
    font-weight: bold;
    color:rgb(214, 214, 214)
  }
</style>
