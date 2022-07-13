<template>
    <header>
        <div id="search-bar" class="search w-100 p-2 d-flex justify-content-between align-items-center">
            <div id="logo">
                <img class='w-100' :src="logo" alt="Netflix">
            </div>
            <div>
                <div id="input" class="input-group">
                    <input type="text" class="form-control" @keyup.enter="$emit('searchBTN', inputText)"
                        v-model="inputText" placeholder="Search Movies or TV Series">
                    <button type="button" class="btn btn-outline-danger p-2"
                        @click="$emit('searchBTN', inputText)">Search
                    </button>
                </div>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name: 'HeaderPage',
    data() {
        return {
            inputText: '',
            logo: require('../assets/img/Netflix-Logo.jpg'),
        };
    },
};
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap';
@import '../assets/style.scss';

.search {
    background-color: $header-color;

    #logo {
        width: 70px;
    }
}
</style>