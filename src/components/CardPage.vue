<template>
    <li id="cards" class="h-100">
        <div class="card position-relative d-flex flex-column">
            <div class=" img-container border border-3 border-white">
                <img :src="loadPoster" :alt="info.title" class="img-fluid w-100 h-100">
            </div>
            <div class="overlay position-absolute text-start w-100 h-100 p-3">
                <div class="info h-100 pt-5 overflow-scroll">
                    <div class="title pb-1">
                        <span class="fw-bold fs-6">Title:</span>
                        <span class="fs-6"> {{ (info.title) ? info.title : info.name }} </span>
                    </div>
                    <div class="original-title pb-1">
                        <span class="fw-bold fs-6">Original Title:</span>
                        <span class="fs-6">{{ (info.original_title) ? info.original_title : info.original_name
                            }}</span>
                    </div>
                    <div class="language pb-1">
                        <LangFlag :iso="info.original_language" v-if="setFlag" />
                        <div v-else>
                            <span class="fw-bold">Unknown Language</span>
                        </div>
                    </div>
                    <div class="vote pb-1">
                        <div class="stars">
                            <span class="text-rating fw-bold fs-6"> Rating: </span>
                            <i v-for="element in 5" :key="element"
                                :class="(element <= ((Math.round(rating)) / 2)) ? 'fas fa-star' : 'far fa-star'" />
                        </div>
                    </div>
                    <div class="plot pb-1">
                        <div v-if="more_info">
                            <div class="overview pb-1" v-if="info.overview !== ''">
                                <span class="fw-bold fs-6">Overview:</span>
                                <span class="fs-6"> {{ info.overview }} </span>
                            </div>
                            <div v-else class="fw-bold fs-6">UnKnown Plot</div>
                        </div>
                    </div>
                    <div class="casting pb-5">
                        <div v-if="more_info">
                            <div class="cast" v-if="getCast(id).length">
                                <span class="fw-bold fs-6">Cast:</span>
                                <span class="fs-6" v-for="(element, index) in getCast(id)" :key="index">
                                    {{ element }}
                                </span>
                            </div>
                            <div v-else class="fw-bold fs-6">UnKnown Cast</div>
                        </div>
                    </div>
                    <div id="btn-info" @click="more_info = !more_info">
                        <div v-if="more_info">
                            <button class="btn btn-danger">Less Info</button>
                        </div>
                        <div v-else>
                            <button class="btn btn-danger">More Info</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </li>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
import '@fortawesome/fontawesome-free/js/all.js';
import axios from 'axios';

export default {
    name: 'CardPage',
    components: {
        LangFlag,
    },
    props: ['info', 'type'],
    data() {
        return {
            urlPoster: 'https://image.tmdb.org/t/p/w342',
            posterPath: this.info.poster_path,
            rating: this.info.vote_average,
            httpRequest: 'https://api.themoviedb.org/3/',
            api_key: '86f3788548eab8efa8a450f86c015b29',
            id: this.info.id,
            cast: [],
            more_info: false,
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
    methods: {
        getCast(id) {
            const bodyRequest = 'credits';
            const parameters = {
                api_key: this.api_key,
            };
            axios.get(`${this.httpRequest}${this.type}/${id}/${bodyRequest}`, { params: parameters })
                .then((result) => {

                    let castList = result.data.cast;
                    this.cast = [];
                    if (castList.length > 0) {
                        for (let i = 0; i < 5; i++) {
                            this.cast.push(castList[i].name);
                        }
                    }
                })
                .catch(() => console.clear());
            return this.cast;
        }
    },
};
</script>

<style lang="scss">
@import '../assets/style.scss';

.card {
    color: white;

    .img-container {
        height: 350px;
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