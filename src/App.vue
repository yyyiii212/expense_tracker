<script setup>
// import { RouterLink, RouterView } from 'vue-router'
import HomeView from './views/HomeView.vue';
import Page from './views/Page.vue';
</script>

<template>
  <!-- <header> -->
  <div class="wrapper">
    <!-- <nav> -->
    <!-- <RouterLink to="/">Home</RouterLink> -->
    <!-- </nav> -->
    <!-- <HomeView /> -->
    <!-- <RouterLink to="/page">Page</RouterLink> -->
  </div>
  <!-- </header> -->

  <RouterView />
</template>

<style scoped></style>
