<template>
  <ShopCard v-for="shop in catalogMain" :key="shop.name" :itemData="shop" />
</template>

<script>
import catalog from "../assets/items.json";
import ShopCard from "./ShopCard.vue";

export default {
  data() {
    return {
      catalogMain: catalog,
    };
  },
  components: { ShopCard },
};
</script>

<style></style>
