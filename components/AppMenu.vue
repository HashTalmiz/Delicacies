<template>
  <nav>
    <ul>
      <li>
        <nuxt-link to="/"><AppLogo /></nuxt-link>
      </li>
      <li><nuxt-link to="/restaurants">Restaurants</nuxt-link></li>
    </ul>
    <div v-if="countCartItems > 0" class="smallnum">{{ countCartItems }}</div>
    <nuxt-link to="/cart">Cart</nuxt-link>
  </nav>
</template>

<script>
import AppLogo from "@/components/AppLogo.vue";
import { mapGetters } from "vuex";

export default {
  components: {
    AppLogo,
  },
  computed: {
    ...mapGetters(["countCartItems"]),
  },
};
</script>

<style lang="sass" scoped>
</style>