<template>
  <div>
    <div class="card shadow border-0">
      <div class="card-body">
        <div class="card-text">
          <div class="row">
            <div class="col-11">
              <h3>{{blog.title}}</h3>
            </div>
            <div class="col-1 text-right" @click="changePage('list')">
              <button class="btn btn-link text-success">
                <i class="fas fa-2x fa-arrow-circle-left"></i>
              </button>
            </div>
          </div>
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