<script>
import AppMain from './components/AppMain.vue';
import { store } from './store'
const endpointMovie = 'https://api.themoviedb.org/3/search/movie?api_key=edcc8a8669f8819a0394b2c8f9a3038c&query=superman'
const endpointSeries = 'https://api.themoviedb.org/3/search/tv?api_key=edcc8a8669f8819a0394b2c8f9a3038c&query=superman'
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
        console.log(movies)
      }))
    },
    fetchSeriesStore() {
      (axios.get(endpointSeries).then(res => {
        const series = res.data.results.map(res => {
          return {
            id: res.id,
            title: res.name,
            originalTitle: res.original_name,
            language: res.original_language,
            vote: res.vote_average,
            text: res.overview,
            date: res.first_air_date,
            img: res.poster_path
          }
        })
        store.series = series
        console.log(series)
      }))
    },
    fetchAllStore() {
      this.fetchMovieStore()
      this.fetchSeriesStore()
    }
  }


}
</script>
<template>
  <AppMain @click-button="fetchAllStore" />
  <!-- fare una funzione che richiama le due fetch axios al click del bottone -->

  <!-- fare registrazione sul sito dei film edcc8a8669f8819a0394b2c8f9a3038c
      {{ ricorda che dopo il query= ci va il nome che l'utente sta cercando }}
      {{ ricorda che per le img guarda l'indirizzo su milestone 3 poi gli metti w342 e poi gli monti di fianco ciò che arriva dall'api
    ricordati che devi inserire tutto in una costante fino al w342 e poi gli monti api }}
    guardare bene postman
  fare uno store con 2 array uno per i film e uno per le serie tv -->
</template>
<style lang="scss">
@use './assets/stylesass/style.scss';
</style>