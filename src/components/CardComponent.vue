<template>
    <div id="cards">
        <div class="card position-relative text-center d-flex flex-column align-items-center">
            <div class=" img-container m-3">
                <img :src="loadPoster" :alt="info.title" class="w-100 h-100 border border-5 border-dark">
            </div>
            <div class="overlay position-absolute w-100 h-100">
                <div class="info h-100 p-2 flex-column">
                    <h2>
                        Title: {{ (info.title) ? info.title : info.name }}
                    </h2>
                    <h3>
                        Original title: {{ (info.original_title) ? info.original_title : info.original_name }}
                    </h3>
                    <LangFlag :iso="info.original_language" v-if="setFlag" />
                    <h4 class="text-center" v-else>
                        <p>unknown language</p>
                    </h4>
                    <div class="vote">
                        <div class="stars d-flex justify-content-center">
                            <span> Rating: </span>
                            <i v-for="element in 5" :key="element"
                                :class="(element <= ((Math.round(rating)) / 2)) ? 'fas fa-star' : 'far fa-star'" />
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
import '@fortawesome/fontawesome-free/js/all.js';

export default {
    name: 'CardPage',
    components: {
        LangFlag,
    },
    props: ['info'],
    data() {
        return {
            urlPoster: 'https://image.tmdb.org/t/p/w342',
            posterPath: this.info.poster_path,
            rating: this.info.vote_average,
        };
    },
    computed: {
        setFlag() {
            if (this.info.original_language === 'sv' ||
                this.info.original_language === 'no' ||
                this.info.original_language === 'nl') {
                return false;
            }
            return true;
        },
        loadPoster() {
            if (this.posterPath === null) {
                return require('../assets/img/Netflix-Logo.jpg')
            }
            return `${this.urlPoster}${this.posterPath}`
        },
    },
};
</script>

<style lang="scss">
@import '../assets/style.scss';

.cards {
    height: 100%;
    overflow: hidden;
}

.card {
    color: white;

    .img-container {
        height: 300px;

        img {
            height: 100%;
        }
    }

    .overlay {
        display: none;
    }
}

.card:hover .overlay {
    display: block;
    opacity: 0.9;
    background-color: black;
}
</style>