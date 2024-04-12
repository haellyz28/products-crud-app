<!-- ProductList.vue -->
<template>
  <div>
    <h2>Product List</h2>
    <div v-for="product in products" :key="product.id" class="product-item">
      <div><strong>Name:</strong> {{ product.name }}</div>
      <div><strong>Description:</strong> {{ product.description }}</div>
      <div><strong>Price:</strong> {{ product.price }}</div>
      <div>
        <button @click="editProduct(product)">Edit</button>
        <button @click="confirmDelete(product)">Delete</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductList',
  props: ['products'],
  methods: {
    editProduct(product) {
      this.$router.push({ name: 'EditProduct', params: { id: product.id }});
    },
    confirmDelete(product) {
      if (confirm('Are you sure you want to delete this product?')) {
        this.deleteProduct(product);
      }
    },
    deleteProduct(product) {
      this.$emit('delete-product', product.id);
    }
  }
}
</script>

<style scoped>
.product-item {
  margin-bottom: 20px;
  padding: 10px;
  border: 1px solid #ccc;
}
.product-item button {
  margin-left: 10px;
}
</style>
