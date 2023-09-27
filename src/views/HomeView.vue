<script setup lang="ts">
  import { onMounted, reactive, ref } from 'vue';
  let characters = reactive(ref());
  import CharacterList from '../components/CharactersList.vue';

  onMounted(() => {
    fetch('https://rickandmortyapi.com/api/character')
      .then((response) => response.json())
      .then(response => {
        characters.value = response.results;
      })
  }) 
</script>

<template>
  <main>
    <div class="list">
      <CharacterList v-for="character in characters" :id="character.id" :name="character.name" :url="character.image" :species="character.species" :gender="character.gender" />
    </div>
  </main>
</template>

<style>
  .list {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1rem;
    margin-top: 1.5rem;
  }
</style>
