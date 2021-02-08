<template>
  <div class="pokemon-list">
    <ul>
      <li v-for="(pkmn, index) in pokemons" :key="index" class="pokemon">
        <Pokemon :name="pkmn.name" :url="pkmn.url"></Pokemon>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Pokemon from "./Pokemon.vue";
import axios from "axios";

@Component({
  components: {
    Pokemon,
  },
})
export default class PokemonList extends Vue {
  pokemons = {};

  async getPokemons(uri: string) {
    return await axios.get(uri, {
      headers: {
        "Content-Type": "application/json",
        "Access-Control-Allow-Origin": "*",
      },
      proxy: {
        host: "104.236.174.88",
        port: 3128,
      },
    });
  }

  created() {
    this.getPokemons("https://pokeapi.co/api/v2/pokemon")
      .then((pokemons) => {
        this.pokemons = pokemons.data.results;
        console.log(this.pokemons);
      })
      .catch((err) => {
        console.error(err);
      });
  }
}
</script>
