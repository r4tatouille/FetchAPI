<script setup>
const props = defineProps({
  page: Number,
  totalPages: Number,
});

const emit = defineEmits("change-page");

function cahngePage(newPage) {
  emit("change-page", newPage);
}
</script>

<template>
  <button
    class="pagination-button"
    id="prevPage"
    @click="cahngePage(page - 1)"
    v-show="page > 1"
  >
    &lt;
  </button>
  <span>Page {{ page }}</span>
  <button
    class="pagination-button"
    id="nextPage"
    @click="cahngePage(page + 1)"
    v-show="page < totalPages"
  >
    &gt;
  </button>
</template>

<style scoped>
.pagination-button {
  background-color: #fff;
  color: #00b894;
  padding: 8px 12px;
  border: none;
  border-radius: 50%;
  cursor: pointer;
  font-size: 16px;
  margin: 0 5px;
}
</style>
