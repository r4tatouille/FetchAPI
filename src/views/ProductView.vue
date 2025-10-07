<template>
  <div class="product-detail">
    <h2>Product title</h2>
    <img
      src="https://placehold.co/600x400"
      alt="product.title"
      class="product-image"
    />
    <p>Product description</p>
    <p>Product price</p>
    <router-link to="/" class="back-button">Back</router-link>
  </div>
</template>

<style scoped>
.product-detail {
  margin-top: 20px;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f9f9f9;
  text-align: center;
}

.product-image {
  max-width: 100%;
  height: auto;
  margin-bottom: 10px;
}

.product-detail p {
  margin-bottom: 5px;
}

.product-detail button {
  margin-top: 10px;
  padding: 10px 10px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.back-button {
  display: inline-block;
  padding: 8px 16px;
  background-color: #007bff;
  color: #fff;
  text-decoration: none;
  border-radius: 4px;
  transition: backgorund-color 0.3s;
}

.back-button:hover {
  background-color: #0056b3;
}
</style>
