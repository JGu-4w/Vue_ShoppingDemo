<template>
  <div class="product-list">
    <product-list-item v-for="(item, index) in productList" :productItem="item" :key="index"></product-list-item>
  </div>
</template>

<script>
import ProductListItem from './ProductListItem';
export default {
  name: 'ProductList',
  components: {
    ProductListItem,
  },
  props: {
    productList: {
      type: Array,
      default() {
        return [];
      }
    }
  }
}
</script>

<style scoped>
  .product-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
  }
</style>