<template>
  <div id="app">
    <HeaderPage @searchBtn="searchMovie" />
    <MainPage :movies="movies" />
  </div>
</template>

<script>

import HeaderPage from './components/HeaderPage.vue';
import MainPage from './components/MainPage.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    HeaderPage,
    MainPage,
  },
  data() {
    return {
      url: 'https://api.themoviedb.org/3/search/movie?api_key=86f3788548eab8efa8a450f86c015b29&query=',
      inputText: '',
      movies: [],
    };
  },
  created() {
    this.searchMovie()
  },
  methods: {
    searchMovie(text) {
      this.inputText = text;
      axios.get(`${this.url}${text}`)
        .then((result) => this.movies = result.data.results)
        .catch((err) => console.log('Error', err));
    }
  },
}
</script>

<style lang="scss">
</style>