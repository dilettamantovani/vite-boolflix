<script>
import { store } from '../store.js'

export default {
    name: 'SearchMovie',
    emits: ["search"],
    data() {
        return {
            store
        }
    },

    methods: {
        searchMovie() {
            this.$emit('search');
        }
    }
}
</script>

<template>
    <h1>Boolflix</h1>
    <input type="text" placeholder="Search..." v-model="store.getInput" @keyup="searchMovie">
</template>

<style scoped>
h1 {
    color: red;
    font-weight: 700;
    font-size: 2rem;
}
</style>