<template>
  <div id="app">
    <HeaderPage />
  </div>
</template>

<script>

import HeaderPage from './components/HeaderPage.vue'
export default {
  name: 'App',
  components: {
    HeaderPage,
  },
  data() {
    return {
      http: 'https://api.themoviedb.org/3/search/',
      apikey: '86f3788548eab8efa8a450f86c015b29',
      body_request: 'movie',
      query: 'signore',
    };
  },
  methods: {

  }
}
</script>

<style lang="scss">
</style>
