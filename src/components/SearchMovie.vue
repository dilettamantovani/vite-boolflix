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
    <h1>BOOLFLIX</h1>
    <input type="text" placeholder="Search..." v-model="store.getInput" @keyup="searchMovie">
</template>

<style scoped>
h1 {
    color: red;
    font-stretch: condensed;
    font-size: 3rem;
    font-weight: 600;
}

input {
    height: 1.6rem;
    width: 15rem;
}
</style>