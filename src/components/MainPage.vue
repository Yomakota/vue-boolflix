<!-- Vogliamo dopo la risposta dell’API visualizzare a schermo i seguenti valori per ogni film trovato:
1. Titolo
2. Titolo Originale
3. Lingua
4. Voto -->

<template>
    <div class="container my-5">
        <div class="row row-cols-5">
            <MovieCard class="mb-3" v-for="element, index in movies" :key="index" :movies="element" />
        </div>
    </div>
</template>
<script>
import MovieCard from './MovieCard.vue';

export default {
    name: 'MainPage',
    components: {
        MovieCard,
    },
    props: ['movies']
}
</script>
<style lang="scss" scoped>
@import '../assets/style.scss';
</style>