<template>
  <div class="container">
    <img src="../assets/logo-pokemon.png" width="215" height="100" alt="Pokemon-Logo"/>

    <PokemonList
    :imageUrl="imageUrl"
    :apiUrl="apiUrl"
    @setPokemonUrl="setPokemonUrl"/>

    <PokemonDetail
    v-if="showDetail"
    :pokemonUrl="pokemonURL"
    :imageUrl="imageUrl"
    @closeDetail="closeDetail"/>

  </div>

</template>

<script>

// Importando os componentes

import PokemonList from './PokemonList.vue'
import PokemonDetail from './PokemonDetail.vue'

export default {
  name: 'Pokemon',
  data: () => {
    return {
      // URL de imagens de pokemóns
      imageUrl: 'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/',
      // API pokeapi
      apiUrl: 'https://pokeapi.co/api/v2/pokemon/',
      pokemonURL: '',
      showDetail: false
    }
  },
  components: {

    PokemonList,
    PokemonDetail
  },
  methods: {
    setPokemonUrl (url) {
      this.pokemonURL = url
      this.showDetail = true
    },
    closeDetail () {
      this.pokemonURL = ''
      this.showDetail = false
    }
  }
}
</script>

<style lang="sass" scoped>
@import url('https://fonts.googleapis.com/css?family=Acme')

.container
    display: flex
    justify-content: center
    align-items: center
    flex-direction: column
    padding: 10px
    width: calc(100% - 20px)
    min-heigth: calc(100vh - 20px)
    background: #ffb800

    font-family: 'Acme', arial
    font-size: 1rem
    font-weight: normal

    img
        margin-bottom: 5%

</style>
