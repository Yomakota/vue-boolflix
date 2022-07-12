<!-- Vogliamo dopo la risposta dell’API visualizzare a schermo i seguenti valori per ogni film trovato:
1. Titolo
2. Titolo Originale
3. Lingua
4. Voto -->

<template>
    <div class="container">
        <div class="row row-cols-5" v-for="element, index in movies" :key="index" :movies="element">
            {{ element.title }}
            {{ element.original_title }}
            {{ element.original_language }}
            {{ element.vote_average }}
        </div>
    </div>
</template>
<script>
export default {
    name: 'MainPage',
    props: ['movies']
}
</script>
<style lang="scss">
@import '../assets/style.scss';
</style>