<template>
  <v-container>
    <!--  bouton de retour-->
    <v-btn @click=" $router.back()">Retour</v-btn>

    <v-alert v-if="!pokemon" type="error">Pokemon non trouvé</v-alert>

    <v-card v-else>
      <v-img
        :src="getImageUrl(pokemon.img)"
        :alt="pokemon.name"
        height="300"
        cover
      />
      <v-card-title>{{ pokemon.name }}</v-card-title>
      <v-card-subtitle>Niveau {{ pokemon.level }}</v-card-subtitle>
      <v-card-text>{{ pokemon.description }}</v-card-text>
    </v-card>

  </v-container>
</template>

<script setup>
import {getImageUrl} from '@/utils/imageUrl'

const route = useRoute()
const pokemons = ref([])

const pokemon = computed(() => {
  return pokemons.value.find(p => p.id === route.params.id)
})

onMounted(async () => {
  const response = await fetch('http://localhost:3535/pokemons');
  pokemons.value = await response.json()
})
</script>

<style scoped>

</style>
