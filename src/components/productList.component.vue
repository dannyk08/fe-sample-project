<template>
  <main class="component main-component">
    <h1 class="products-header">Shop Our Featured Collection</h1>
    <ul class="products-list">
      <ProductListItem 
        v-for="product in products" 
        v-bind:key="product.id"
        v-bind:productDetail="product" />
    </ul>
  </main>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
import ProductListItem from "./productListItem.component.vue";

export default {
  name: "Products",
  computed: mapGetters({
    products: "allProducts"
  }),
  components: {
    ProductListItem
  },
  created() {
    this.$store.dispatch("getAllProducts");
  }
};
</script>

<style scoped>
.products-list {
  display: flex;
  flex-wrap: wrap;
  padding: 0;
  list-style: none;
}
</style>
