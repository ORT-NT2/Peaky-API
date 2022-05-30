<template>
  <div class="card" style="width: 18rem">
    <img :src="pokemon.picture" alt="..." class="card-img-top" />
    <div class="card-body">
      <h5 class="card-title">
        <b>{{ pokemon.name }}</b>
      </h5>
      <div class="d-flex justify-content-between">
        <span>{{ pokemon.name }}</span>
      </div>
      <div class="d-flex justify-content-between">
        <span>{{}}</span>
      </div>
      <div class="d-flex justify-content-between">
        <span>{{}}</span>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "CharacterList",
  props: {
    pokemon: Object,
  },
  data() {
    return {
      sprite: String,
    };
  },
  methods: {
    async loadCharacterData(url) {
      const res = await axios.get(url)
      this.sprite = res.data.sprites.front_default
    },
  },
  watch:{
    pokemon:{
      handler: function (val, oldVal) { 
        this.loadCharacterData(val.url)
      }
    }
  },
  created() {
    this.loadCharacterData(this.pokemon.url)
  },
};
</script>