<template>
  <div id="app">

  <Header 
  @searchedFilms="search"
  />

  <main class="d-flex flex-wrap">
    <Movies
    v-for="(movie,index) in movieAndSeries" 
    :key="index"
    :poster="movie.poster_path"
    :titolo="movie.title ? movie.title : movie.name"
    :titoloOriginale="movie.original_title ? movie.original_title : movie.original_name"
    :lingua="movie.original_language"
    :voto="movie.vote_average"
    :overview="movie.overview"/>

    <h1 v-if="movieAndSeries.length == 0 && !searching"> Comincia la tua ricerca per iniziare a guardare tutte le serie tv e i film che vuoi   
    </h1>
  </main>
  
  </div>
</template>

<script>
import Header from './components/Header';
import Movies from './components/Movies';

import axios from 'axios';


export default {
  name: 'App',
  components: {
    Header,
    Movies
  },
  data() {
    return {
      newFilm: '',
       movies: [],
       series: [],
        api_key:"api_key=e99307154c6dfb0b4750f6603256716d",
        api_url:"https://api.themoviedb.org/3/search/movie?",
        api_series_url:"https://api.themoviedb.org/3/search/tv?",
        query: '',
        searching: false
    }
  },
  methods: {
    search(string) {
       this.query = string;
      axios.all([
      axios
      .get(`${this.api_url}${this.api_key}&query=${this.query}`),

      axios
      .get(`${this.api_series_url}${this.api_key}&query=${this.query}`)
      ])

      .then(axios.spread((res1, res2)=>{
      this.movies = res1.data.results;
      this.series = res2.data.results;}))
     
    }
  },
  computed: {
      movieAndSeries() {
        return[...this.movies, ...this.series];
      },
  },
}

</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.min.css';
@import '~bootstrap/scss/bootstrap';


main {
  justify-content: space-between;

    h1 {
      color: red;
      text-align: center;
      margin-top: 10%;
    }
}

</style>
