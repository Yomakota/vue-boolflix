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
    return {
      httpRequest: 'https://api.themoviedb.org/3/search/',
      api_key: '86f3788548eab8efa8a450f86c015b29',
      language: 'en-US',
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
      const bodyRequest = 'movie';
      const parameters = {
        api_key: this.api_key,
        language: this.language,
        query: this.searchText,
      };

      axios.get(`${this.httpRequest}${bodyRequest}`, { params: parameters })
        .then((result) => {
          this.movies = result.data.results;
          console.log(this.movies);
        })
        .catch((error) => console.log(error));
    },
    searchTV() {
      const bodyRequest = 'tv';
      const parameters = {
        api_key: this.api_key,
        language: this.language,
        query: this.searchText,
      };

      axios.get(`${this.httpRequest}${bodyRequest}`, { params: parameters })
        .then((result) => {
          this.tvs = result.data.results;
          console.log(this.tvs);
        })
        .catch((error) => console.log(error));
    },
  },
};
</script>

<style lang="scss">
@import './assets/style.scss';
</style>