<template>
    <div class="container">
        <form action="submit"></form>
        <input type="text" v-bind="id">
    </div>
</template>


<script>
export default {
name: "PokemonList",
data () {
    return {
        id: null
    }
}
}
</script>