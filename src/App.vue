<template>
  <div id="app">
    <HeaderPage @searchBTN="search" />
    <MainPage :movies="movies" :tvs="tvs" />
  </div>
</template>

<script>
import axios from 'axios';
import HeaderPage from './components/HeaderPage.vue';
import MainPage from './components/MainPage.vue';

export default {
  name: 'App',
  components: {
    HeaderPage,
    MainPage,
  },
  data() {
    // https://api.themoviedb.org/3/search/movie?api_key=86f3788548eab8efa8a450f86c015b29&language=en-US&query=
    // https://api.themoviedb.org/3/search/tv?api_key=86f3788548eab8efa8a450f86c015b29&language=it_IT&query=
    // https://image.tmdb.org/t/p/w342
    return {
      httpRequest: 'https://api.themoviedb.org/3/search/',
      bodyRequest: 'movie?',
      bodyRequestTv: 'tv?',
      api_key: 'api_key=86f3788548eab8efa8a450f86c015b29&',
      language: 'en-US',
      query: 'query=',
      searchText: '',
      movies: [],
      tvs: [],
    };
  },
  methods: {

    search(text) {
      this.searchText = text;
      this.searchMovie();
      this.searchTV();
    },
    searchMovie() {

      axios.get(`${this.httpRequest}${this.bodyRequest}${this.api_key}${this.query}${this.searchText}`)
        .then((result) => {
          this.movies = result.data.results;
        })
        .catch((error) => console.log(error));
    },
    searchTV() {
      axios.get(`${this.httpRequest}${this.bodyRequestTv}${this.api_key}${this.query}${this.searchText}`)
        .then((result) => {
          this.tvs = result.data.results;
        })
        .catch((error) => console.log(error));
    }
  },
};
</script>

<style lang="scss">
@import './assets/style.scss';

body {
  background-color: $bg-color;
}
</style>