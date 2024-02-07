<script>
import AppMain from './components/AppMain.vue';
import { store } from './store'
const endpointMovie = 'https://api.themoviedb.org/3/search/movie?api_key=edcc8a8669f8819a0394b2c8f9a3038c&query=superman'
import axios from 'axios';
export default {
  name: 'App Boolflix',
  data: () => ({
    store
  }),
  components: { AppMain },
  methods: {
    fetchMovieStore() {
      (axios.get(endpointMovie).then(res => {
        const movies = res.data.results.map(res => {
          return {
            id: res.id,
            title: res.title,
            originalTitle: res.original_title,
            language: res.original_language,
            vote: res.vote_average,
            text: res.overview,
            date: res.release_date,
            img: res.poster_path
          }
        })
        store.movies = movies
      }))
    },
    fetchSeriesStore() {

    }
  }


}
</script>
<template>
  <AppMain @click-button="fetchMovieStore" />
  <div>
    <!-- fare registrazione sul sito dei film edcc8a8669f8819a0394b2c8f9a3038c
      {{ ricorda che dopo il query= ci va il nome che l'utente sta cercando }}
      {{ ricorda che per le img guarda l'indirizzo su milestone 3 poi gli metti w342 e poi gli monti di fianco ciò che arriva dall'api
    ricordati che devi inserire tutto in una costante fino al w342 e poi gli monti api }}
    guardare bene postman
  fare uno store con 2 array uno per i film e uno per le serie tv -->
  </div>
</template>
<style lang="scss">
@use './assets/stylesass/style.scss';
</style>