<template>
  <div class="pokemon">
    <h2>{{ name }}</h2>
    <img :src="pokemon.sprites.front_default" :alt="name" />
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import axios from "axios";

@Component
export default class Pokemon extends Vue {
  @Prop() name!: string;
  @Prop() url!: string;

  pokemon = {};

  async getPokemon() {
    return await axios.get(this.url, {
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
    this.getPokemon()
      .then((pokemon) => {
        this.pokemon = pokemon.data;
        console.log(this.pokemon);
      })
      .catch((err) => {
        console.error(err);
      });
  }
}
</script>
