

<template>

</template>

<script setup>
const route = useRoute().params.id
const pokemon = fetch('http://localhost:3535/pokemons')
pokemon.find()


</script>

<style scoped>

</style>
