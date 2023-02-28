<template>
    <div class="max-w-screen-xl mx-auto p-4">
      <h1 class="text-2xl font-bold mb-4">Buscar personajes de Rick and Morty</h1>
      <form class="mb-4" @submit.prevent="searchCharacters">
        <input
          type="text"
          class="w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
          placeholder="Buscar personajes..."
          v-model="searchTerm"
        />
      </form>
      <ul>
        <li v-for="character in characters" :key="character.id" class="mb-4">
          <div class="flex items-center">
            <img :src="character.image" class="w-20 h-20 rounded-full mr-4" />
            <div>
              <h2 class="text-xl font-bold">{{ character.name }}</h2>
              <p class="text-gray-500">{{ character.species }} - {{ character.status }}</p>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        searchTerm: '',
        characters: [],
      };
    },
    methods: {
      async searchCharacters() {
        const response = await axios.get(
          `https://rickandmortyapi.com/api/character/?name=${this.searchTerm}`
        );
        this.characters = response.data.results;
      },
    },
  };
  </script>  