<template>
  <div class="container">
        <input type="text" id="myInput" onkeyup="myFunction()" placeholder="Search for pokemons..">
       <table>

        <thead>

          <tr>
            <th>NOME</th>
            <th>QTD</th>
          </tr>

        </thead>

        <tbody>

           <tr id="myUL" v-for="(pokemon, index) in pokemons" :key="index" class="pokemon">



            <div class="pokemon-picture">
              <img :src="pokemons[index].sprites.front_default" :alt="pokemons[index].name">
            </div>
            <td>{{ pokemons[index].name }}</td>
            <td>{{ pokemons[index].weight }}</td>



          </tr>

        </tbody>

      </table>

  </div>
</template>

<script>
const axios = require('axios');
let offset =  1, limit = 14;

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
