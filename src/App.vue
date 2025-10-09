<script setup>
import { RouterLink, RouterView } from "vue-router";
import HomeView from "./views/HomeView.vue";
</script>

<template>
  <!-- <router-link to="/">Home</router-link>
  <router-link to="/about">About</router-link> -->
  <!-- <RouterView /> -->
  <suspense>
    <template #default>
      <router-view />
    </template>
    <template #fallback>
      <p>Loading...</p>
    </template>
  </suspense>
</template>
