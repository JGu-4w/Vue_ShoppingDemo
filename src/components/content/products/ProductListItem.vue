<template>
  <div class="product-list-item" @click="itemClick">
    <img :src="getImage" alt="" @load="itemLoaded">
    <div class="product-info">
      <p>{{productItem.title}}</p>
      <span class="price">{{productItem.price}}</span>
      <span class="collect">{{productItem.cfav}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductListItem',
  props: {
    productItem: {
      type: Object,
      default() {
        return {};
      }
    }
  },
  computed: {
    getImage() {
      return this.productItem.image || this.productItem.show.img;
    }
  },
  methods: {
    itemLoaded() {
      if(this.$route.path.indexOf('/home') !== -1) {
        this.$bus.$emit('homeItemLoaded');
      } else if (this.$route.path.indexOf('/detail') !== -1){
        this.$bus.$emit('detailItemLoaded');
      }
    },
    itemClick() {
      if(this.productItem.item_id) {
        this.$router.push('/detail/' + this.productItem.item_id);
      } else {
        this.$router.push('/detail/' + this.productItem.iid);
      }
    }
  }
}
</script>

<style scoped>
  .product-list-item {
    position: relative;
    width: 48%;
  }

  img {
    width: 100%;
    height: 85%;
    border-radius: 3%;
  }

  .product-info {
    font-size: 12px;
    text-align: center;
  }

  .product-info p {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    margin-bottom: 3px;
  }

  .product-info span {
    text-align: center;
  }

  .product-info .price {
    color: var(--color-high-text);
    margin-right: 20px;
  }

  .product-info .collect {
    position: relative;
  }

  .product-info .collect::before {
    position: absolute;
    width: 14px;
    height: 14px;
    left: -15px;
    content: '';
    background: url('~assets/img/common/collect.svg') 0 0/14px 14px;
  }
</style>