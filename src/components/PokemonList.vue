<template>
  <div class="container">
    <div class="row justify-content-center">
      <div :key="p.id" v-for="p in pokemons" class="col-4 mt-4">
        <PokemonCard :pokemon="p" />
      </div>
    </div>
    <div class="button-group">
      <button id="btnPrev" class="button" @click="prev()">Previous</button>
      <button id="btnNext" class="button" @click="next()">Next</button>
    </div>
  </div>
</template>

<script>
import PokemonCard from "./PokemonCard.vue";
import axios from "axios";

export default {
  name: "PokemonList",
  components: {
    PokemonCard,
  },
  data() {
    return {
      pokemons: [],
      urls: { prev: null, next: null },
    };
  },
  methods: {
    async loadPokemons(url = "https://pokeapi.co/api/v2/pokemon/") {
      const res = await axios.get(url);
      const { results, previous, next } = res.data;
      this.pokemons = results;
      this.urls.prev = previous;
      this.urls.next = next;
      document.getElementById("btnPrev").disabled = !this.urls.prev;
      document.getElementById("btnNext").disabled = !this.urls.next;
    },
    async prev() {
      this.loadPokemons(this.urls.prev);
    },
    async next() {
      this.loadPokemons(this.urls.next);
    },
  },
  created() {
    this.loadPokemons();
  },
};
</script>