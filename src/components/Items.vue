<!-- Main Component -->
<template>
  <div class="items">
    <Item v-for="item in items" :item="item" :key="item.ItemID"></Item>
  </div>
</template>

<script>
// Components
import Item from "./Item";

export default {
  name: "Items",
  components: {
    Item
  },
  props: {
    items: Array
  }
};
</script>
<style lang="less">
@import "../assets/less/colors.less";

.items {
  display: flex;
  align-content: flex-start;
  justify-content: center;
  overflow-y: auto;
  flex-wrap: wrap;
  height: 850px; // Define Height for flex wrap container
}

.items::-webkit-scrollbar {
  width: 14px;
  height: 14px;
}

.items::-webkit-scrollbar-track {
  background-color: transparent;
}

.items::-webkit-scrollbar-thumb {
  border-radius: 15px;
}

.items::-webkit-scrollbar-thumb {
  background-color: @border;
}

.items::-webkit-scrollbar-thumb:hover {
  background-color: @itemBorderHover;
}

.items::-webkit-scrollbar-thumb {
  background-clip: padding-box;
}

.items::-webkit-scrollbar-thumb {
  border: 4px solid transparent;
}

.items::-webkit-scrollbar-thumb {
  min-height: 44px;
}
</style>
