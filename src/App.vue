<!-- App.vue -->
<template>
  <div id="app">
    <router-view :products="products" @add-product="addProduct" @delete-product="deleteProduct"/>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      products: [
        { id: 1, name: 'Product 1', description: 'Description 1', price: 10 },
        { id: 2, name: 'Product 2', description: 'Description 2', price: 20 },
        { id: 3, name: 'Product 3', description: 'Description 3', price: 30 }
      ]
    };
  },
  methods: {
    addProduct(newProduct) {
      this.products.push(newProduct);
    },
    deleteProduct(productId) {
      this.products = this.products.filter(product => product.id !== productId);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
