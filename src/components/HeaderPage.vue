<template>
    <header>
        <div
            class="search-bar fixed-top
                d-flex
                justify-content-between
                align-items-center
                w-100 p-2"
        >
            <div id="logo">
                <img class='w-100' :src="logo" alt="Netflix">
            </div>
            <div>
                <div id="input" class="input-group">
                    <input type="text"
                            class="form-control text-uppercase"
                            v-model="inputText"
                            placeholder="search your show"
                            @keyup.enter="sendInputText()"
                        >
                    <button type="button"
                            class="btn btn-outline-danger p-2"
                            @click="sendInputText()">Search
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
    methods: {
        sendInputText() {
            this.$emit("sendText", this.inputText);
            this.inputText = "";
        },
    },
};
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap';
@import '../assets/style.scss';

.search-bar {
    background-color: $header-color;

    input {
        background-color: transparent;
        border: none;

        &::placeholder {
            color: red;
        }

    }

    #logo {
        width: 70px;
    }
}
</style>