<script>
import axios from 'axios'
import Buscador from './Buscador.vue'


let API_URL = `https://rickandmortyapi.com/api/character`

export default {
    data() {
        return {
            info: [],
            personajes: [],
            cont: 2
        };
    },
    mounted() {
        axios.get(API_URL)
            .then((response) => {
            this.info = response.data.info;
            this.personajes = response.data.results;
        });
    },
    methods: {
        pag(num) {
            API_URL = "https://rickandmortyapi.com/api/character/?page=" + num;
            console.log(API_URL);
            axios.get(API_URL)
                .then((response) => {
                console.log(response.config);
                this.info = response.data.info;
                this.personajes = response.data.results;
            });
            this.cont++;
        }
    },
    components: { Buscador }
}

</script>

<template>
  
  <div>
  
  <div class="flex items-center font-bold ... w-120 rounded overflow-hidden shadow-lg p-12 m-10 snap-start bg-teal-400">
  <h2>Hay {{ info.count }} personajes en el programa de Rick & Morty </h2>

  <button @click="pag(cont)"> página {{ cont }}</button>
  </div>
  
<div class="flex items-center font-bold ... w-120 rounded overflow-hidden shadow-lg p-12 m-10 snap-start bg-teal-400">
  
  <body class="antialiased bg-gray-200 text-gray-900 font-sans p-6">
  
    
    <Buscador/>
    <div class="flex flex-wrap justify-center">
      
    <ul class="p-10 grid grid-cols-1 sm:grid-cols-1 md:grid-cols-3 lg:grid-cols-3 xl:grid-cols-4 gap-5">
    
    <li v-for="p in personajes" class="w-120 rounded overflow-hidden shadow-lg p-12 m-10 snap-start bg-teal-400">
      <img v-bind:src="p.image"  alt="no image">
      <a>{{ p.name }} id:{{ p.id }}</a> 
    </li> 



    </ul>
    </div>





</body>



  </div>
</div>
</template>