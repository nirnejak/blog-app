<template>
  <div class="list-group">
    <div v-for="blog in blogs" :key="blog.id" class="list-group-item border-0 shadow my-2">
      <div class="row">
        <div class="col-8">
          <p>{{blog.title}}</p>
        </div>
        <div class="col-4 text-right pt-2">
          <span class="p-3" @click="changePage('details', blog.id)">
            <i class="fas fa-eye"></i>
          </span>
          <span class="p-3">
            <i class="fas fa-pencil-alt"></i>
          </span>
          <span class="p-3">
            <i class="fas fa-trash-alt"></i>
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "BlogList",
  data() {
    return {
      blogs: []
    };
  },
  props: ["changePage"],
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/posts/")
      .then(res => {
        this.blogs = res.data;
      })
      .catch(error => console.log(error));
  }
};
</script>

<style>
</style>