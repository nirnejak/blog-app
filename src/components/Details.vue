<template>
  <div>
    <div class="card shadow border-0">
      <div class="card-body">
        <div class="card-text">
          <h3>{{blog.title}}</h3>
          <p>{{blog.body}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Details",
  data() {
    return {
      blog: {}
    };
  },
  props: ["changePage", "id"],
  created() {
    axios
      .get(`https://jsonplaceholder.typicode.com/posts/${this.$props.id}`)
      .then(res => {
        this.blog = res.data;
      })
      .catch(error => console.log(error));
  }
};
</script>

<style>
</style>