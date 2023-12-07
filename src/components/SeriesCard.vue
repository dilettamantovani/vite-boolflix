<script>
import { store } from '../store.js';

export default {
    name: 'SeriesCard',
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
        <section v-if="store.series.length > 0">
            <h2>Series</h2>
        </section>

        <section class="wrapper">
            <div class="card" v-for="series in store.series">
                <div class="card-inner">
                    <div class="card-front">
                        <img class="poster" :src="`https://image.tmdb.org/t/p/w342/${series.poster_path}`"
                            onerror="this.src='https://placehold.co/600x800?text=Image+Not+Found'" alt="">

                    </div>

                    <div class="card-back">
                        <h3>{{ series.name }}</h3>
                        <h6><em>(Original Title: {{ series.original_name }})</em></h6>
                        <p><em>(Original Language: <img class="flag" :src="getFlag(series.original_language)" alt="">)</em>
                        </p>
                        <div class="stars">
                            <i v-for="i in 5" :class="{ 'filling': i <= getVote(series.vote_average) }"
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