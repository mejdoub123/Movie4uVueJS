<template>
  <div class="movie-card">
    <h4>{{ movie.title }}</h4>
    <div class="img-movie">
      <img
        :src="movie.image_url"
        alt="Movie Image"
        style="width: 100%; height: 100%"
      />
    </div>
  </div>
</template>
<script>
export default {
  name: "MovieItem",
  props: {
    movie: Object,
  },
};
</script>
<style scoped>
.movie-card {
  width: 50%;
  position: relative;
  color: rgb(39, 2, 73);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  align-self: center;
}
.movie-card h4 {
  text-align: center;
  margin: 5px 8px;
  padding: 7px 5px;
  background-color: rgb(197, 189, 199);

  opacity: 0.8;
  border-radius: 6px;
  position: absolute;
  top: 5%;
}
</style>
