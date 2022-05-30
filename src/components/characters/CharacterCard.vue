<template>
  <div class="card" style="width: 18rem">
    <img :src="character.picture" alt="..." class="card-img-top" />
    <div class="card-body">
      <h5 class="card-title">
        <b>{{ character.name }}</b>
      </h5>
      <div class="d-flex justify-content-between">
        <span>{{ character.name }}</span>
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
    character: Object,
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
    character:{
      handler: function (val, oldVal) { 
        this.loadCharacterData(val.url)
      }
    }
  },
  created() {
    this.loadCharacterData(this.character.url)
  },
};
</script>