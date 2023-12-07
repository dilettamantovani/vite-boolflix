<script>
import { store } from '../store.js';

export default {
    name: 'MovieCard',
    data() {
        return {
            store,
        }
    },

    props: {
        movie: Object
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
    <main>
        <section v-if="store.movies.length > 0">
            <h2>Movies</h2>
        </section>

        <section class="wrapper">
            <div class="card" v-for="movie in store.movies">
                <div class="card-inner">
                    <div class="card-front">
                        <img class="poster" :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" alt="">
                        <!-- inserisci v-if/else per poster: null -->
                    </div>

                    <div class="card-back">
                        <h3>{{ movie.title }}</h3>
                        <h6><em>(Original Title: {{ movie.original_title }})</em></h6>
                        <p><em>(Original Language: <img class="flag" :src="getFlag(movie.original_language)" alt="">)</em>
                        </p>
                        <div class="stars">
                            <i v-for="i in 5" :class="{ 'filling': i <= getVote(movie.vote_average) }"
                                class="fa-solid fa-star"></i>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </main>
</template>

<style scoped>
.flag {
    width: 1.5rem;
}

.filling {
    color: yellow;
}
</style>