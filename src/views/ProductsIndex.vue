<template>
  <div class="products-index">
    <div class="row">    
      <div class="card" v-for="product in products">
        <div class="card" style="width: 18rem;">
         <!-- <img class="card-img-top" v-bind:src= alt="Card image cap"> -->
          <div class="card-body">
            <h5 class="card-title">{{ product.name }}</h5>
            <h5 class="card-text">Price: {{ product.price }}</h5>
            <p class="card-text">Description: {{ product.description }}</p>
          </div>
          <router-link class="btn btn-primary" v-bind:to"'/products/' + product.id"> More Info</router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
</style>

<script>
  var axios = require('axios');
export default {
  data: function() {
    return {
      products: []
    };
  },
  created: function() {
    axios
    .get("http://localhost:3000/api/products")
    .then(response => {
      this.products = response.data;
    });

  },
  methods: {},
  computed: {}
};
</script>
