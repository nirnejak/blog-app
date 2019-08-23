<template>
  <div id="app">
    <div class="container">
      <h1 class="text-light">My Blog</h1>
      <hr class="bg-light" />

      <BlogList v-if="currentPage === 'list'" :changePage="changePage" />
      <Details v-if="currentPage === 'details'" :changePage="changePage" :id="id" />
      <Form v-if="currentPage === 'create'" :changePage="changePage" />
      <Form v-if="currentPage === 'edit'" :changePage="changePage" :id="id" />
    </div>
  </div>
</template>

<script>
import BlogList from "./components/BlogList";
import Details from "./components/Details";
import Form from "./components/Form";

export default {
  name: "app",
  data() {
    return {
      currentPage: "list",
      id: null
    };
  },
  components: {
    BlogList,
    Details,
    Form
  },
  methods: {
    changePage: function(page, id) {
      console.log("hel")
      this.currentPage = page;
      if (id) {
        this.id = id;
      }
    }
  }
};
</script>

<style>
body {
  background-image: radial-gradient(
    circle farthest-corner at 10% 20%,
    rgba(55, 227, 181, 1) 0%,
    rgba(78, 228, 126, 0.54) 90%
  );
  background-size: cover;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
