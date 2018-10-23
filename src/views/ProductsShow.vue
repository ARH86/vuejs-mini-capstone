<template>
  <div class="products-show">
    <h2>{{ product.name }}</h2>
    <h4>{{ product.description }}</h4>
    <img v-bind:src="product.image_url" v-bind:alt="product.name">
    
  </div>
</template>

<style>
</style>

<script>
  var axios = require('axios');

export default {
  data: function() {
    return {
            product: {
              price: {
               description: {

               }
              }
            }
    };
  },
  created: function() {
    axios
    .get("http://localhost:3000/api/products/" + this.$route.params.id)
    .then(response => {
      this.product = response.data;
    });


  },
  methods: {},
  computed: {}
};
</script>