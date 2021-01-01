<template>
  <main class="container restaurant">
    <div class="restaurantheading">
      <h1>Restaurants</h1>
      <AppSelect
        select="Restaurant"
        :selectOptions="this.options"
        @change="selectedRestaurant = $event"
      />
    </div>

    <AppRestaurantInfo :dataSource="filteredRestaurants" />
  </main>
</template>

<script>
import AppRestaurantInfo from "@/components/AppRestaurantInfo.vue";
import AppSelect from "@/components/AppSelect.vue";
import { mapState } from "vuex";

export default {
  components: {
    AppRestaurantInfo,
    AppSelect,
  },
  data() {
    return {
      selectedRestaurant: "",
      options: ["Pizza", "Dim Sum", "Taco"],
    };
  },
  computed: {
    ...mapState(["fooddata"]),
    filteredRestaurants() {
      if (this.selectedRestaurant) {
        return this.fooddata.filter((el) => {
          let name = el.name.toLowerCase();
          return name.includes(this.selectedRestaurant.toLowerCase());
        });
      }
      return this.fooddata;
    },
  },
};
</script>

<style lang="scss" scoped>
</style>