<template>
  <NavBar @search-movies="searchMovies" />
  <router-view :movies="movies" />
</template>
<script>
import NavBar from "./components/NavBar.vue";
export default {
  components: {
    NavBar,
  },
  data() {
    return {
      movies: [],
      movie: {},
    };
  },
  methods: {
    async searchMovies(text) {
      this.movies = [];
      const res = await fetch(
        `https://data-imdb1.p.rapidapi.com/movie/imdb_id/byTitle/${text}/`,
        {
          method: "GET",
          headers: {
            "x-rapidapi-host": "data-imdb1.p.rapidapi.com",
            "x-rapidapi-key":
              "586db6afc6msh007cc4eedf7796ap163debjsnd1a17be1e269",
          },
        }
      );

      const data = await res.json();

      for (
        let i = 0;
        data.results.length > 20 ? i < 20 : i < data.results.length;
        i++
      ) {
        this.movies.push(await this.searchMovie(data.results[i].imdb_id));
      }

      console.log(this.movies);
    },

    async searchMovie(id) {
      const res = await fetch(
        `https://data-imdb1.p.rapidapi.com/movie/id/${id}/`,
        {
          method: "GET",
          headers: {
            "x-rapidapi-host": "data-imdb1.p.rapidapi.com",
            "x-rapidapi-key":
              "586db6afc6msh007cc4eedf7796ap163debjsnd1a17be1e269",
          },
        }
      );

      const data = await res.json();

      return data.results;
    },
  },
};
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins&display=swap");
* {
  font-family: "Poppins", sans-serif;
}
</style>
