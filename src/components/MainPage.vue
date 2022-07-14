<template>
    <main>
        <div class="main-container-fluid">
            <section id="movies">
                <h2 v-if="movies.length"
                    class="text-center text-uppercase my-3 p-2"
                >
                    Movies
                </h2>
                <ul class="row flex-nowrap">
                    <CardPage v-for="(card, index) in movies" :key="index + card.id" :info="card" type="movie" class="col-2"
                />
                </ul>
            </section>
            <section id="tv-series">
                <h2 v-if="tvs.length"
                    class="text-center text-uppercase my-3 p-2"
                >
                    TV Series
                </h2>
                <ul class="row flex-nowrap">
                    <CardPage v-for="(card, index) in tvs" :key="index + card.id" :info="card"
                    type="tv" class="col-2"
                />
                </ul>
            </section>
        </div>
        <div id="welcome"
            class="position-absolute top-50 start-50 translate-middle
            text-center text-decoration-underline fs-1"
            v-if="movies.length === 0 && tvs.length === 0"
        >
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

.main-container-fluid {
    margin-top: 100px;
}

#movies,
#tv-series {
    h2 {
        position: fixed;
        font-family: $font-family;
        background-color: $header-color;
        opacity: 0.5;
        color: $title-text;
        z-index: 999;
    }
}

#movies {
    h2 {
        top: 9%;
    }
}

#tv-series {
    h2 {
        top: 46%;
    }
}

#welcome {
    color: $title-text;
    font-family: $font-family;
}
</style>