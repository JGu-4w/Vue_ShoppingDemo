<template>
  <div id="tab-bar">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "TabBar",
}
</script>

<style scoped>
  #tab-bar {
    display: flex;
    position: fixed;
    left: 0;
    right: 0;
    bottom: 0;
    width: 100vw;
    height: 49px;
    background-color: #f6f6f6;
    box-shadow: 0 -1px 3px rgba(0, 0, 0, .1);
    /* z-index: 9; */
  }
</style>