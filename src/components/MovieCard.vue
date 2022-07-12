<template>
    <div class="cards">
        <div class="card d-flex flex-column align-items-center h-100 p-3">
            <div>{{ movies.title }}</div>
            <div>{{ movies.title }}</div>
            <div>{{ movies.original_language }}</div>
            <div>{{ movies.vote_average }}</div>
        </div>
    </div>
</template>
<script>
import MovieCard from './MovieCard.vue';
export default {
    name: MovieCard,
    props: ['movies']
}
</script>
<style lang="scss" scoped>
@import '../assets/style.scss';
</style>