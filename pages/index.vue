<template>
  <main class="container">
    <AppHeader />
    <app-restaurant-info></app-restaurant-info>
  </main>
</template>

<script>
import AppHeader from "@/components/AppHeader.vue";
import AppRestaurantInfo from "@/components/AppRestaurantInfo.vue";

export default {
  components: {
    AppHeader,
    AppRestaurantInfo,
  },
};
</script>

<style>
</style>