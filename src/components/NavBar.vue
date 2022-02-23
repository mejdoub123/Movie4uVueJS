<template>
  <div class="nav-container">
    <div class="icon-title">
      <i class="fa-solid fa-clapperboard fa-2xl"></i>
      <h1>Movie4u</h1>
    </div>
    <div v-show="homePage" class="search-container">
      <input type="text" v-model="text" placeholder="Search a movie..." />
      <i @click="onClick" class="fa-solid fa-magnifying-glass"></i>
    </div>
    <div class="nav-items">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </div>
  </div>
</template>
<script>
export default {
  name: "NavBar",
  data() {
    return {
      text: "",
    };
  },
  computed: {
    homePage() {
      if (this.$route.path === "/") {
        return true;
      } else {
        return false;
      }
    },
  },
  methods: {
    onClick(e) {
      e.preventDefault();
      if (!this.text) {
        console.log("Please enter a show");
        return;
      }
      console.log(this.text);
      this.$emit("search-movies", this.text);
      this.text = "";
    },
  },
};
</script>
<style scoped>
.nav-container {
  display: flex;
  justify-content: space-between;
  height: 60px;
  width: 100%;
  box-shadow: rgba(0, 0, 0, 0.45) 0px 5px 20px -20px;
}
.icon-title {
  display: flex;
  align-items: center;
}
.icon-title h1 {
  padding: 4px 10px;
  color: rgb(84, 28, 136);
}
.fa-clapperboard {
  padding: 4px 10px;
  color: rgb(84, 28, 136);
}
.fa-magnifying-glass {
  color: rgb(183, 142, 221);
  cursor: pointer;
}
.fa-magnifying-glass:hover {
  color: rgb(149, 101, 194);
}
.search-container {
  display: flex;
  align-items: center;
  background-color: rgb(244, 241, 255);
  padding: 0px 10px;
  height: 40px;
  border-radius: 5px;
  align-self: center;
}
.search-container input {
  border: none;
  outline: none;
  background-color: transparent;
}
.nav-items {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.nav-items a {
  text-decoration: none;
  padding: 0px 10px;
  color: rgb(138, 55, 216);
}
</style>
