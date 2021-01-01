<template>
  <main class="container cart">
    <h2>Cart</h2>
    <div v-if="cart.length === 0" class="container">
      <AppHungryMan />
      <h3>Your cart is empty</h3>
      <nuxt-link to="/restaurants">
        <button class="primary">Fill it up!</button>
      </nuxt-link>
    </div>
    <table v-else>
      <thead>
        <tr>
          <th>Item</th>
          <th>Add Ons</th>
          <th>Amount</th>
          <th>Total Price</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in cart" :key="item.id">
          <td>
            {{ item.item }}
            <span v-if="item.options">- {{ item.options }}</span>
          </td>
          <td>
            <span v-for="addon in item.addOns" :key="addon" class="comma">{{
              addon
            }}</span>
          </td>
          <td>{{ item.count }}</td>
          <td>{{ item.combinedPrice }}</td>
        </tr>
        <tr>
          <td colspan="3"></td>
          <td class="total">Total: ${{ totalCartValue.toFixed(2) }}</td>
        </tr>
      </tbody>
    </table>
  </main>
</template>

<script>
import { mapState, mapGetters } from "vuex";
import AppHungryMan from "@/components/AppHungryMan.vue";

export default {
  computed: {
    ...mapState(["cart"]),
    ...mapGetters(["totalCartValue"]),
  },
};
</script>

<style lang="scss" scoped>
</style>