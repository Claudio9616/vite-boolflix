<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from './store'
const endpointMovie = 'https://api.themoviedb.org/3/search/movie?api_key=edcc8a8669f8819a0394b2c8f9a3038c&query='
const endpointSeries = 'https://api.themoviedb.org/3/search/tv?api_key=edcc8a8669f8819a0394b2c8f9a3038c&query='
import axios from 'axios';
export default {
  name: 'App Boolflix',
  data: () => ({
    store
  }),
  components: { AppMain, AppHeader },
  methods: {
    fetchMovieStore(endpoint) {
      (axios.get(endpoint).then(res => {
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
    fetchSeriesStore(endpoint) {
      (axios.get(endpoint).then(res => {
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
    fetchAllStore(event) {
      const searchAllMovie = `${endpointMovie}${event}`
      const searchAllSeries = `${endpointSeries}${event}`
      this.fetchMovieStore(searchAllMovie)
      this.fetchSeriesStore(searchAllSeries)
    }
  }


}
</script>
<template>
  <AppHeader @search-terms="fetchAllStore" />

  <!-- adesso in app main scarica lo store , fai le props per le card con il v-bind da passare a suo figlio e fai un v-for su template dei films e uno sulle serie  -->
  <!-- fare registrazione sul sito dei film edcc8a8669f8819a0394b2c8f9a3038c
      {{ ricorda che per le img guarda l'indirizzo su milestone 3 poi gli metti w342 e poi gli monti di fianco ciò che arriva dall'api
    ricordati che devi inserire tutto in una costante fino al w342 e poi gli monti api }}-->
</template>
<style lang="scss">
@use './assets/stylesass/style.scss';
</style>