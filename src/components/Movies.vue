<template>
  <div class="movies-container" :key="movie.imdb_id" v-for="movie in movies">
    <MovieItem :movie="movie" />
  </div>
</template>
<script>
import MovieItem from "./MovieItem.vue";
export default {
  name: "MoviesComponent",
  components: {
    MovieItem,
  },
  props: {
    movies: Array,
  },
};
</script>
<style scoped>
.movies-container {
  display: flex;
  justify-content: center;
  align-items: center;
  align-self: center;
  width: 70%;
}
</style>
