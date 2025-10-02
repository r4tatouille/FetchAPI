<script setup>
import ProductCard from "@/components/ProductCard.vue";
import Pagination from "@/components/Pagination.vue";

import {
  onMounted,
  onBeforeMount,
  onBeforeUpdate,
  ref,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from "vue";
import axios from "axios";

async function getProducts(params) {
  const response = await axios.get("http://localhost:3000/products");
  console.log(response.data);
}

getProducts();
// const page = ref(1);

// function nextPage() {
//   page.value++;
// }

// onBeforeMount(() => {
//   console.log("Component will be mounted soon");
// });

// onMounted(() => {
//   console.log("Component has been mounted");
// });

// onBeforeUpdate(() => {
//   console.log("Component will be updated soon");
// });

// onUpdated(() => {
//   console.log("Component has been updated");
// });

// onBeforeUnmount(() => {
//   console.log("Component will be mounted soon");
// });

// onUnmounted(() => {
//   console.log("Component has been unmounted");
// });
</script>

<template>
  <main>
    <!-- {{ page }}
    <button @click="nextPage">Next</button> -->
    <div class="product-grid">
      <ProductCard />
    </div>
    <div class="pagination">
      <Pagination />
    </div>
  </main>
</template>

<style scoped>
.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 20px;
  width: 80%;
  margin: 0 auto;
}

.pagination {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}
</style>
