<script>
import axios from 'axios'
let API_URL = `https://rickandmortyapi.com/api/character`

export default {
  data() {
    return {
      info: [],
      personajes: [],
      pagina:1,
      siguiente:null,
      anterior:null,
      mostrarCard: false,
      buscar:'',
    }
  },
  mounted() {
    axios.get(API_URL)
      .then((response) => {
        this.info = response.data.info;
        this.personajes = response.data.results;
      })
  },
  
  methods: {
    navpag(num) {
      API_URL='https://rickandmortyapi.com/api/character/?page='+(this.pagina +"&&name="+this.buscar)
      console.log(API_URL)
      axios.get(API_URL)
      .then((response) => {
        console.log(response.config)
        this.info = response.data.info;
        this.personajes = response.data.results;
      })
    },
    buscador(text) {
      API_URL='https://rickandmortyapi.com/api/character/?'+('name='+text ||'&status='+text)
      console.log(API_URL)
      axios.get(API_URL)
      .then((response) => {
        console.log(response.config)
        this.info = response.data.info;
        this.personajes = response.data.results;
      })
    },

  },
}

</script>

<template >

  <div class="text-center" >
    
  <h2 style="margin: 100px 10px 10px 10px">Hay {{ info.count }} personajes en el programa de Rick & Morty</h2>

  

  
  <div class="flex items-center font-bold ... w-120 rounded overflow-hidden shadow-lg p-12 m-10 snap-start bg-[#fbcfe8]">



<body class="antialiased bg-gray-200 text-gray-900 font-sans p-6">

  
  <Buscador/>
  <div class="flex flex-wrap justify-center">
    <input v-model="buscar" placeholder="Buscar personaje..." style="margin: 10px 10px 10px 10px" class="leading-tight text-blue-700 border border-blue focus:outline-none focus:shadow-outline shadow appearance-none border rounded" />
  <button @click="buscador(buscar) " class="bg-[#1da1f2] hover:bg-[#0c4a6e] text-white font-bold py-1 px-4 rounded-full lg:inline-block">Buscar</button>

  <ul class="p-5 grid grid-cols-1 sm:grid-cols-1 md:grid-cols-3 lg:grid-cols-3 xl:grid-cols-10 gap-5">
  
  <li v-for="p in personajes" class="text-sm w-120 rounded overflow-visible shadow-lg p- m-1 snap-start bg-[#bfdbfe]">
    <img v-bind:src="p.image"  alt="no image">
    <a>{{ p.name }} id:{{ p.id }}</a> 
    
    
  </li> 

  
  <li class="absolute insert-0" v-if="mostrarCard">
  <Card :dato="personajes" @click="ocultarCard"/>
  
  </li>


  </ul>
  </div>

</body>


<div>
</div>

</div>

  </div>
  <button class="bg-[#1da1f2] hover:bg-[#0c4a6e] text-white font-bold py-1 px-4 rounded-full lg:inline-block" v-if="pagina!==1" @click="navpag(pagina--)">Anterior</button>
  
  <a class="rounded-full w-10 h-10">{{pagina }}</a>
  <button class="bg-[#1da1f2] hover:bg-[#0c4a6e] text-white font-bold py-1 px-4 rounded-full lg:inline-block" v-if="pagina!==this.info.pages" @click="navpag(pagina++)">Siguiente</button>
  

</template>


