<script>
export default {
    name: 'MovieCard',
    props: {
        movie: Object
    },

    methods: {
        getFlag(lang) {
            return new URL(`../assets/flags/${lang}.png`, import.meta.url).href
        },

        getStars(vote) {
            return Math.ceil(vote / 2)
        },
    },


}
</script>

<template>
    <div class="card">
        <img class="poster" :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" alt="">
        <h3>{{ movie.title }}</h3>
        <h6><em>(Original Title: {{ movie.original_title }})</em></h6>
        <p><em>(Original Language: <img class="flag" :src="getFlag(movie.original_language)" alt="">)</em></p>
        <h4>{{ movie.vote_average }}</h4>
    </div>
</template>

<style scoped>
.poster {
    width: 13.7rem;
    padding: 0.5rem;
}

.flag {
    width: 1.5rem;
}
</style>