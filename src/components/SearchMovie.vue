<script>
import { store } from '../store.js'

export default {
    name: 'SearchMovie',
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
    <div>
        <input type="text" placeholder="Search..." v-model="store.getInput" @keyup="searchMovie">
    </div>
    <!-- language? -->
</template>

<style scoped></style>