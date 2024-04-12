<!-- AddProductForm.vue -->
<template>
  <div>
    <h2>Add Product</h2>
    <form @submit.prevent="addProduct">
      <div>
        <label for="name">Name:</label>
        <input v-model="name" type="text" id="name" required>
      </div>
      <div>
        <label for="description">Description:</label>
        <textarea v-model="description" id="description" required></textarea>
      </div>
      <div>
        <label for="price">Price:</label>
        <input v-model.number="price" type="number" id="price" required>
      </div>
      <button type="submit">Add Product</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'AddProductForm',
  data() {
    return {
      name: '',
      description: '',
      price: null
    };
  },
  methods: {
    addProduct() {
      const newProduct = {
        id: Date.now(),
        name: this.name,
        description: this.description,
        price: this.price
      };
      this.$emit('add-product', newProduct);
      this.name = '';
      this.description = '';
      this.price = null;
    }
  }
}
</script>

<style scoped>
form {
  margin-top: 20px;
}
label {
  display: block;
  margin-bottom: 5px;
}
input[type="text"],
textarea,
input[type="number"] {
  width: 100%;
  padding: 8px;
  margin-bottom: 10px;
}
button {
  padding: 10px 20px;
  background-color: #007bff;
  color: #fff;
  border: none;
  cursor: pointer;
}
</style>
