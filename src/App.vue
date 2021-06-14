<template>
  <div id="app">

  <Header 
  @searchedFilms="search"
  />

  <main>
    <Movies
    v-for="(movie,index) in movies" 
    :key="index"
    :item="movie"
    />
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
        api_key:"api_key=e99307154c6dfb0b4750f6603256716d",
        api_url:"https://api.themoviedb.org/3/search/movie?",
        query: '',
    }
  },
  methods: {
    search(string) {
       this.query = string;
      axios
      .get(`${this.api_url}${this.api_key}&query=${this.query}`)
      .then((res) => {
      this.movies = res.data.results;
      console.log(this.movies);
      });
    }
  }
}

</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.min.css';
@import '~bootstrap/scss/bootstrap';


</style>
