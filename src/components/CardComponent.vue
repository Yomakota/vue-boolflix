<template>
    <li id="cards" class="h-100">
        <div class="card position-relative d-flex flex-column">
            <div class=" img-container border border-3 border-white">
                <img :src="loadPoster" :alt="info.title" class="img-fluid w-100 h-100">
            </div>
            <div class="overlay text-start position-absolute w-100 h-100 p-3">
                <div class="info h-100 pt-5">
                    <div class="title">
                        <span class="fw-bold fs-6">Title:</span>
                        <span class="fs-6"> {{ (info.title) ? info.title : info.name }} </span>
                    </div>
                    <div class="original-tile">
                        <span class="fw-bold fs-6">Original Title:</span>
                        <span class="fs-6">{{ (info.original_title) ? info.original_title : info.original_name
                        }}</span>
                    </div>
                    <LangFlag :iso="info.original_language" v-if="setFlag" />
                    <div v-else>
                        <span class="fw-bold">Unknown Language</span>
                    </div>
                    <div class="vote">
                        <div class="stars">
                            <span class="text-rating fw-bold fs-6"> Rating: </span>
                            <i v-for="element in 5" :key="element"
                                :class="(element <= ((Math.round(rating)) / 2)) ? 'fas fa-star' : 'far fa-star'" />
                        </div>
                    </div>
                    <div class="overview">
                        <span class="fw-bold fs-6">Overview:</span>
                        <span class="fs-6"> {{ info.overview }} </span>
                    </div>
                </div>
            </div>
        </div>
    </li>
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
            urlPoster: 'https://image.tmdb.org/t/p/original',
            posterPath: this.info.poster_path,
            rating: this.info.vote_average,
        };
    },
    computed: {
        setFlag() {
            if (this.info.original_language === 'it' ||
                this.info.original_language === 'en' ||
                this.info.original_language === 'us' ||
                this.info.original_language === 'ko') {
                return true;
            }
            return false;
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

.card {
    color: white;

    .img-container {
        height: 600px;
    }

    .overlay {
        display: none;

        .stars {
            color: $stars;

            .text-rating {
                color: white;
            }
        }
    }
}

.card:hover .overlay {
    display: block;
    opacity: 0.9;
    background-color: black;
}
</style>