<template>
  <div class="product-new">
    <div class="container">
      <form v-on:submit.prevent="submit()">
        <h1>Create a Product</h1>
        <ul>
          <li class="text-danger" v-for="error in errors">{{ error }}</li>
        </ul>
        <div class="form-group">
          <label>Name:</label> 
          <input type="text" class="form-control" v-model="name">
        </div>
        <div class="form-group">
          <label>Price:</label>
          <input type="text" class="form-control" v-model="price">
          <h6>Input price</h6>
        </div>
        <div class="form-group">
          <label>Description:</label>
          <input type="text" class="form-control" v-model="description">
          <h6>Input description</h6>
        </div>
        <div class="form-group">
          <label>Image URL:</label>
          <input type="text" class="form-control" v-model="imageURL">
        </div>
        <input type="submit" class="btn btn-primary" value="Submit">
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      name: "",
      price: "",
      description: "",
      imageURL: "",
      errors: []
    };
  },
  methods: {
    submit: function() {
      var params = {
        name: this.name,
        price: this.price,
        description: this.description,
        image_url: this.imageURL
      };
      axios
        .post("http://localhost:3000/api/products", params)
        .then(response => {
          this.$router.push("/recipes/" + response.data.id);
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>
