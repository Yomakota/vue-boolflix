<template>
    <main>
        <div class="container">
            <section id="movies">
                <h2 v-if="movies.length > 0" class="text-center text-uppercase my-3 p-2">
                    Movies
                </h2>
                <ul class="row g-5 row-cols-3">
                    <CardComponent v-for="(card, index) in movies" :key="index + card.id" :info="card" />
                </ul>
            </section>
            <section id="tv-series">
                <h2 v-if="tvs.length > 0" class="text-center text-uppercase my-3 p-2">
                    TV Series
                </h2>
                <ul class="row g-5 row-cols-3">
                    <CardComponent v-for="(card, index) in tvs" :key="index + card.id" :info="card" />
                </ul>
            </section>
        </div>
    </main>
</template>

<script>
import CardComponent from './CardComponent.vue';
export default {
    name: 'MainPage',
    components: {
        CardComponent,
    },
    props: ['movies', 'tvs']
};
</script>

<style lang="scss" scoped>
@import '../assets/style.scss';

h2 {
    font-family: $font-family;
    background-color: $header-color;
    color: $title-text;
}
</style>