<script setup>
import ProductCard from "@/components/ProductCard.vue";
import Pagination from "@/components/Pagination.vue";
import Loading from "@/components/Loading.vue";
import ProductForm from "@/components/ProductForm.vue";

import {
  onMounted,
  onBeforeMount,
  onBeforeUpdate,
  ref,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
  watchEffect,
} from "vue";
import axios, { post } from "axios";
import { watch } from "vue";

const products = ref([]);
const page = ref(1);
const limit = ref(8);
const isLoading = ref(true);

async function fetchData() {
  const API_URL = `http://localhost:3000/products?_page=${page.value}&_per_page=${limit.value}`;
  try {
    isLoading.value = true;
    const response = await axios.get(API_URL);
    products.value = response.data;
  } catch (error) {
    console.error(error);
  } finally {
    isLoading.value = false;
  }
}

watchEffect(() => {
  fetchData();
});

function changePage(newPage) {
  if (newPage < 1) return;
  if (newPage > products.value.totalPages) return;
  page.value = newPage;
}

async function createProduct(product) {
  try {
    await axios.post("http://localhost:3000/products", product);
    fetchData();
  } catch (error) {
    console.error(error);
  }
}
// onMounted(async () => {
//   try {
//     products.value = await axios.get(API_URL).then((res) => res.data);
//   } catch (error) {
//     console.log(error);
//   } finally {
//     isLoading.value = false;
//   }
// });

// watch(page, async () => {
//   try {
//     isLoading.value = true;
//     products.value = await axios.get(API_URL).then((res) => res.data);
//   } catch (error) {
//     console.log(error);
//   } finally {
//     isLoading.value = false;
//   }
// });

// console.log(products.value);

// async function getProducts(params) {
//   const response = await axios.get("http://localhost:3000/products");
//   products.value = response.data;
//   console.log(response.data);
// }

// getProducts();
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
  <div v-if="isLoading">
    <Loading />
  </div>
  <main v-else>
    <!-- {{ page }}
    <button @click="nextPage">Next</button> -->
    <ProductForm @create-product="createProduct" />
    <div class="product-grid">
      <ProductCard
        v-for="(product, index) in products.data"
        :key="index"
        :product="product"
      />
    </div>
    <div class="pagination">
      <Pagination
        :page="page"
        :totalPages="products.pages"
        @change-page="changePage"
      />
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
