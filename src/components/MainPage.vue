<template>
    <main>
        <div class="container position-relative">
            <section id="movies">
                <h2 v-if="movies.length" class="text-center text-uppercase my-3 p-2">
                    Movies
                </h2>
                <ul class="row g-5 row-cols-3">
                    <CardPage v-for="(card, index) in movies" :key="index + card.id" :info="card" type="movie" />
                </ul>
            </section>
            <section id="tv-series">
                <h2 v-if="tvs.length" class="text-center text-uppercase my-3 p-2">
                    TV Series
                </h2>
                <ul class="row g-5 row-cols-3">
                    <CardPage v-for="(card, index) in tvs" :key="index + card.id" :info="card" type="tv" />
                </ul>
            </section>
        </div>
        <div id="welcome"
            class="position-absolute top-50 start-50 translate-middle text-center text-decoration-underline fs-1"
            v-if="movies.length === 0 && tvs.length === 0">
            Enjoy the show
        </div>
    </main>
</template>

<script>
import CardPage from './CardPage.vue';
export default {
    name: 'MainPage',
    components: {
        CardPage,
    },
    props: ['movies', 'tvs']
};
</script>

<style lang="scss" scoped>
@import '../assets/style.scss';

#welcome {
    color: $title-text;
    font-family: $font-family;
}

h2 {
    font-family: $font-family;
    background-color: $header-color;
    color: $title-text;
}
</style>