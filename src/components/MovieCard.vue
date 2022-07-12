<template>
    <div class="cards">
        <div class="card d-flex flex-column align-items-center h-100 p-3">
            <div>{{ movies.title }}</div>
            <div>{{ movies.title }}</div>
            <!-- <div>{{ movies.original_language }}</div> -->

            <!-- Milestone 2:
            Trasformiamo la stringa statica della lingua in una vera e propria bandiera della nazione corrispondente,gestendo il caso in cui non abbiamo la bandiera della nazione ritornata dall’API. -->
            <lang-flag :iso="movies.original_language" v-if="setFlag" />
            <div class="text-center" v-else>
                <p>no language available
                    <!--{{movies.original_language}}-->
                </p>
            </div>
            <div>{{ movies.vote_average }}</div>
        </div>
    </div>
</template>
<script>

import LangFlag from 'vue-lang-code-flags';

export default {
    name: 'MovieCard',
    components: {
        LangFlag,
    },
    props: ['movies'],
    data() {
        return {
            original_language: '',
        }
    },
    computed: {
        setFlag() {
            if (this.movies.original_language === 'sv' || this.movies.original_language === 'no') {
                return false;
            }
            return true;
        }
    }
}
</script>
<style lang="scss" scoped>
@import '../assets/style.scss';
</style>