<template>
  <div id="app">
    <div class="container">
      <div class="text-center">
        <h2 class="text-center mt-5">КИНОПОИСК🍿</h2>
        <p>Следите за самыми популярными мультфильмами и аниме, которые в тренде.</p>
      </div>

      <div class="my-4">
        <a href="#" @click="getTrendingMovies('3')" class="mx-3 h4">
          Мультфильмы</a
        >
        <a href="#" @click="getTrendingMovies('4')" class="mx-3 h4"
          >Аниме</a
        >
      </div>

      <div class="row" v-if="movies.length > 0">
        <div class="col-md-3" v-for="(movie, i) in movies" :key="i">
          <movie-card :movie="movie" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import MovieCard from "./components/MovieCard.vue";
export default {
  name: "App",
  components: {
    MovieCard,
  },
  data() {
    return {
      movies: [],
      apiKey: "PA12R92-7HTM5N7-Q9W7CRH-F2JRYF8",
    };
  },
  methods: {
    getTrendingMovies(category) {
      return fetch(
        `https://api.kinopoisk.dev/v1.3/movie?page=1&limit=10&typeNumber=${category}`,
        {
          headers: {
            "X-API-KEY": "PA12R92-7HTM5N7-Q9W7CRH-F2JRYF8"
          }
        }
      )
        .then((response) => {
          if (!response.ok) {
            throw new Error(`Network response was not ok: ${response.status} ${response.statusText}`);
          }
          console.log(response);
          return response.json();
        })
        .then((data) => {
          console.log(data.docs);
          this.movies = data.docs;
        });
    },
  },
  mounted() {
    this.getTrendingMovies("3");
  },
};
</script>