<template>
    <header>
        <div class="search-bar w-100 p-3">
            <div class="d-flex justify-content-between align-items-center">
                <div class="logo">
                    <img class='w-100' :src="logo" alt="Netflix-logo">
                </div>
                <div>
                    <input @keyup.enter="$emit('searchBTN', inputText)" v-model="inputText" type="text"
                        placeholder="Inserisci un testo">
                    <button type="button" class="btn btn-outline-danger" @click="$emit('searchBTN', inputText)">Search
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

.search-bar {
    background-color: black;
}

.logo {
    width: 70px;
}
</style>