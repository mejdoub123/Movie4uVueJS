<template>
  <div class="home-container">
    <Movies :movies="movies" />
  </div>
</template>

<script>
import Movies from "../components/Movies.vue";
export default {
  name: "HomeView",
  props: {
    movies: Array,
  },
  components: {
    Movies,
  },
};
</script>
<style scoped>
.home-container {
  margin-top: 2rem;
  justify-content: center;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  align-content: center;
  grid-gap: 1rem;
  align-items: center;
  width: 100%;
}
</style>
