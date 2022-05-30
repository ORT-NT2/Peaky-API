<template>
  <div>
    <PokemonSelector />
    <CharacterList />
  </div>
</template>

<script>
import CharacterList from "./components/CharacterList.vue";
import PokemonSelector from "./components/PokemonSelector.vue";

export default {
  name: "App",
  components: {
    CharacterList,
    PokemonSelector,
  },
};
</script>