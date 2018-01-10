<template lang="pug">
  #app
    section.section
      nav.nav.has-shadow
        .container
          input.input.is-large(
            v-model="searchQuery",
            type="text",
            placeholder="Buscar canciones"
          )
          a.button.is-info.is-large(@click="search") Buscar
          a.button.is-danger.is-large &times;

      .container
        .columns
          .column(v-for="t in tracks") Cancion: {{ t.name }} | Artista: {{ t.artist }}
        .columns
          .column {{ searchMessage }}
</template>

<script>
const tracks = [
  { name: 'Muchacha', artist: 'Luis Alberto Spinetta' },
  { name: 'Hoy aca en el baile', artist: 'El papo' },
  { name: 'I was mande for loving you', artist: 'Kiss' }
]
export default {
  name: 'app',
  data () {
    return {
      searchQuery: '',
      tracks: []
    }
  },

  computed: {
    searchMessage () {
      return `Encontrados: ${this.tracks.length}`
    }
  },

  methods: {
    search () {
      this.tracks = tracks
    }
  }
}
</script>

<style lang="scss">
  @import './scss/main.scss';

</style>
