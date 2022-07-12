<!-- Milestone 1:
Creare un layout base con una searchbar (una input e un button) in cui possiamo scrivere completamente o parzialmente il nome di un film. Possiamo, cliccando il bottone, cercare sull’API tutti i film che contengono ciò che ha scritto l’utente.-->

<template>
    <header>
        <div>
            <input type="text" placeholder="Search Movie" v-model="inputText">
            <button @click="$emit('searchBtn', inputText)">
                Search
            </button>
        </div>
    </header>
</template>
<script>
export default {
    name: 'HeaderPage',
    data() {
        return {
            inputText: '',
        }
    }
}
</script>
<style lang="">

</style>