<!-- EditProductForm.vue -->
<template>
  <div>
    <h2>Edit Product</h2>
    <form @submit.prevent="editProduct">
      <div>
        <label for="edit-name">Name:</label>
        <input v-model="editedProduct.name" type="text" id="edit-name" required>
      </div>
      <div>
        <label for="edit-description">Description:</label>
        <textarea v-model="editedProduct.description" id="edit-description" required></textarea>
      </div>
      <div>
        <label for="edit-price">Price:</label>
        <input v-model.number="editedProduct.price" type="number" id="edit-price" required>
      </div>
      <button type="submit">Save Changes</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'EditProductForm',
  props: ['product'],
  data() {
    return {
      editedProduct: { ...this.product }
    };
  },
  methods: {
    editProduct() {
      this.$emit('edit-product', this.editedProduct);
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
  background-color: #28a745;
  color: #fff;
  border: none;
  cursor: pointer;
}
</style>
