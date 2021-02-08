<template>
  <div id="app">
    <h2>Pokedex</h2>
    <PokemonList></PokemonList>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import PokemonList from "@/components/PokemonList.vue";

@Component({
  components: {
    PokemonList,
  },
})
export default class App extends Vue {}
</script>
