<script>
import { store } from './store.js';
import axios from 'axios';

import MovieCard from './components/MovieCard.vue';
import SeriesCard from './components/SeriesCard.vue';
import SearchMovie from './components/SearchMovie.vue';

export default {
  components: {
    MovieCard,
    SeriesCard,
    SearchMovie,
  },

  data() {
    return {
      store,
    }
  },

  mounted() {
    this.getMovies();
  },

  methods: {
    getMovies() {
      const movieOptions = {
        method: 'GET',
        url: "https://api.themoviedb.org/3/search/movie?api_key=2c8fb11c079446c9942c260e3ac58689&query=",
        params: { query: `${this.store.getInput}`, include_adult: 'false', language: 'en-US', page: '1' },
        headers: {
          accept: 'application/json',
          authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIyYzhmYjExYzA3OTQ0NmM5OTQyYzI2MGUzYWM1ODY4OSIsInN1YiI6IjY1NmRjMDgzNTFmOTlhMDBlMzQ2MTZlNSIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.z1IXoUYx9rCmya2KI-KQr7RYhmTe_z1aiphW4IuA7vM'
        },
      };

      axios
        .request(movieOptions)
        .then(function (response) {
          console.log(response.data.results);
          store.movies = response.data.results;
        })
        .catch(function (error) {
          console.error(error);
        });


      const seriesOptions = {
        method: 'GET',
        url: "https://api.themoviedb.org/3/search/tv?api_key=2c8fb11c079446c9942c260e3ac58689&query=",
        params: { query: `${this.store.getInput}`, include_adult: 'false', language: 'en-US', page: '1' },
        headers: {
          accept: 'application/json',
          authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIyYzhmYjExYzA3OTQ0NmM5OTQyYzI2MGUzYWM1ODY4OSIsInN1YiI6IjY1NmRjMDgzNTFmOTlhMDBlMzQ2MTZlNSIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.z1IXoUYx9rCmya2KI-KQr7RYhmTe_z1aiphW4IuA7vM'
        },
      };

      axios
        .request(seriesOptions)
        .then(function (response) {
          console.log(response.data.results);
          store.series = response.data.results;
        })
        .catch(function (error) {
          console.error(error);
        });

    }

  },
}


</script>

<template>
  <main>
    <h1>Boolflix</h1>

    <SearchMovie @search="getMovies" />
    <h2>Movies</h2>
    <section class="wrapper" id="moviesContainer">
      <MovieCard v-for="movie in store.movies" :movie="movie" />
    </section>
    <h2>Series</h2>
    <section class="wrapper" id="seriesContainer">
      <SeriesCard v-for="series in store.series" :series="series" />
    </section>
  </main>
</template>

<style scoped>
main {
  width: 95%;
  margin: 0 auto;
}

.wrapper {
  display: flex;
  flex-wrap: wrap;
  width: 85%;
  margin: 0 auto;
  justify-content: space-evenly;
  /* overflow-x: auto  da mettere con nowrap*/
}
</style>
