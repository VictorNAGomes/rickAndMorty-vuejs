<script setup lang="ts">
import { onMounted, reactive, ref } from 'vue';
import { useRoute } from 'vue-router';

  const route = useRoute();
  const id = route.params.id;
  let character:any = ref({})


  fetch('https://rickandmortyapi.com/api/character/'+id)
    .then((response) => response.json())
    .then(response => {
      character.value = response;
    })

</script>

<template>
  <main class="characterMain">
    <RouterLink class="home-link" to="/"><img src="../assets/voltar.png" alt="voltar"></RouterLink>
    <div class="card cardCharacter">

      <img
      :src="character.image"
      class="characterImageBig"
      alt="Imagem Character"
      />
      <h1>{{ character.name }}</h1>
      <h2>{{ character.species }}</h2>
      <h2>{{ character.gender }}</h2>
      <h2>{{ character.origin.name }}</h2>
      <h2 :class="{ 'h2-green': character.status == 'Alive', 'h2-red': character.status == 'Dead'}">{{ character.status }}</h2>

    </div>
  </main>
</template>

<style>
  .home-link {
    margin-top: 1.5rem;
    margin-right: 2rem;
  }

  .characterMain {
    display: flex;
    justify-content: center;
  }

  .cardCharacter {
    width: max-content;
    padding: 1.5rem 3rem;
    margin-top: 1.5rem;
  }

  .characterImageBig {
    height: 200px;
    width: 200px;
    border-radius: 50%;
    margin-bottom: 1rem;
  }

  .h2-green {
    color: green;
  }

  .h2-red {
    color: red;
  }
</style>
