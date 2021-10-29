<template>
  <div class="container">

      <p>{{pokemons.name}}</p>
      

  </div>
</template>

<script>
const axios = require('axios');

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
            const response = await axios.get('https://pokeapi.co/api/v2/pokemon/pikachu');
            this.pokemons = response.data;
       }
    }
}
</script>
