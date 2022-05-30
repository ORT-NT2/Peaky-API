<template>
  <div>
    <PokemonSelector />
    <PokemonList />
  </div>
</template>

<script>
import PokemonList from "./components/PokemonList.vue";
import PokemonSelector from "./components/PokemonSelector.vue";

export default {
  name: "App",
  components: {
    PokemonList,
    PokemonSelector,
  },
};
</script>