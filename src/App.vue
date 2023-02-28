<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import Personajes from './components/Personajes.vue'
import Cabecera from './components/Cabecera.vue'
import Card from './components/Card.vue'

</script>

<template>

 

  <header>

    <div>
        <nav class="p-5 shadow md:flex md:items-center md:justify-between">
      <div class="flex justify-between items-center">
      
       
      </div>
  
        <div class="md:flex md:items-center z-[-1] md:z-auto md:static absolute w-full left-0 md:w-auto md:py-0 py-4 md:pl-0 pl-7 md:opacity-100 opacity-0 top-[-400px] transition-all ease-in duration-500">
        
        <RouterLink to="/" class="bg-[#1da1f2] hover:bg-[#0c4a6e] text-white font-bold py-1 px-4 rounded-full lg:inline-block">Home</RouterLink> 
        <RouterLink to="/about" class="bg-[#1da1f2] hover:bg-[#0c4a6e] text-white font-bold py-1 px-4 rounded-full lg:inline-block">About</RouterLink>
        <RouterLink to="/personajes" class="bg-[#1da1f2] hover:bg-[#0c4a6e] text-white font-bold py-1 px-4 rounded-full lg:inline-block">Personajes</RouterLink>
     
          
        </div>
    </nav>
    <Cabecera/>
   
    
    </div>
  </header>
  

  <RouterView />
</template>


