<template>
    <main>
        <div class="container d-flex my-5">
            <div v-if="movies || tvs">
                <div v-show="movies">
                    <div v-if="movies.length > 0" class="row row-cols-5">
                        <CardComponent v-for="(card, index) in movies" :key="index + '-' + card.id" :info="card" />
                    </div>
                    <div v-else>

                    </div>
                </div>
                <div v-show="tvs">
                    <div v-if="tvs.length > 0" class="row row-cols-5">
                        <CardComponent v-for="(card, index) in tvs" :key="index + '-' + card.id" :info="card" />
                    </div>
                    <div v-else>

                    </div>
                </div>
            </div>
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
</style>