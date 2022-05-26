<template>
<div class="fundo bg-gray-200">
  <div class="container flex flex-wrap gap-5 justify-around ml-8">
    

        <div id="myUL" v-for="(pokemon, index) in pokemons" :key="index" class="bg-white mt-8 mb-8 w-1/3 max-w-sm rounded overflow-hidden shadow-lg">

          



            
              <img :src="pokemons[index].sprites.front_default" :alt="pokemons[index].name" class="object-contain h-48 w-48 w-full">

              <div class="bg-red-600">
                <div class="font-mono text-center text-yellow-400 uppercase font-bold text-xl mb-2">{{ pokemons[index].name }}</div>
                  <div class="flex px-6 pt-4 pb-2 flex-wrap justify-center">
                    
                    <span class="w-1/2 bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2 capitalize">Type: {{ pokemons[index].types.map(item => item.type.name).toString()}}</span>
                    <span class="w-1/2 bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2 capitalize">Weight: {{ pokemons[index].weight / 10}}kg</span>
                    <span class="w-1/2  bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2 capitalize">Height: {{ pokemons[index].height / 10}}m</span>
                  </div>
              </div>


  

        </div>

      

    </div>
  </div>

</template>

<script>
const axios = require('axios');
let offset =  1, limit = 50;

export default {

    data() {
        return{
            pokemons: []
        }
    },

    mounted(){
        this.getPokemons();
    },

    methods: {
        async getPokemons(){
          for(let index = 0; index <= limit; index++) {
            const response = await axios.get(`https://pokeapi.co/api/v2/pokemon/${index + offset}`);
            this.pokemons.push(response.data);





       }
    }
  }





}

</script>
