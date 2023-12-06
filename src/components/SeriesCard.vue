<script>
export default {
    name: 'SeriesCard',
    props: {
        series: Object
    },

    methods: {
        getFlag(lang) {
            return new URL(`../assets/flags/${lang}.png`, import.meta.url).href
        },

        getVote(vote) {
            return Math.ceil(vote / 2)
        },
    },

}
</script>

<template>
    <div class="card" id="seriesCard">
        <img class="poster" :src="`https://image.tmdb.org/t/p/w342/${series.poster_path}`" alt="">
        <h3>{{ series.name }}</h3>
        <h6><em>(Original Title: {{ series.original_name }})</em></h6>
        <p><em>(Original Language: <img class="flag" :src="getFlag(series.original_language)" alt="">)</em></p>
        <i v-for="i in 5" :class="{ 'filling': i <= getVote(series.vote_average) }" class="fa-solid fa-star"></i>
    </div>
</template>

<style scoped>
#seriesCard {
    background-color: blueviolet;
}

.poster {
    width: 13.7rem;
    padding: 0.5rem;
}

.flag {
    width: 1.5rem;
}

.filling {
    color: yellow;
}
</style>