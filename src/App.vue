<template>
  <div>
    <CharacterList />
  </div>
</template>

<script>
import CharacterList from "./components/characters/CharacterList.vue";

export default {
  name: "App",
  components: {
    CharacterList,
  },
};
</script>