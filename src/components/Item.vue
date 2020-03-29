<!-- Item Component -->
<template>
  <div class="item" :class="{'expanded': item.showMoreData}">
    <img
      class="icon-close"
      src="../assets/icons/icon-close.png"
      v-if="item.showMoreData"
      @click="showLess"
    />
    <img class="icon" :src="item.icon" @click="showMore" />
    <div class="item-name" :title="item.ItemName" @click="showMore">{{ item.ItemName }}</div>
    <div class="details-container">
      <div class="base-price">Price: ${{ item.BasePrice }}</div>
      <div class="item-id">Item Id: {{ item.ItemID }}</div>
      <div class="dimensions">Dimensions: {{ item.Dimensions }}</div>
      <div class="description" v-if="item.Description">About: {{ item.Description}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Item",
  props: {
    item: Object
  },
  methods: {
    showMore: function() {
      if (this.item.showMoreData) {
        return;
      }
      this.item.showMoreData = true;
    },
    showLess: function() {
      this.item.showMoreData = false;
    }
  }
};
</script>
<style lang="less">
@import "../assets/less/grid.less";
@import "../assets/less/colors.less";

.item {
  .grid;
  .grid-template-rows(10px 20px min-content 10px);
  .grid-template-columns(10px min-content 10px);
  border: 2px solid @border;
  border-radius: 6px;
  margin-right: 20px;
  margin-bottom: 20px;

  .details-container {
    display: none;
  }

  .icon,
  .icon-close,
  .item-name {
    &:hover {
      cursor: pointer;
    }
  }

  .icon {
    .grid-row(3);
    .grid-column(2);
    height: 200px;
    width: 200px;
    padding-top: 10px;
  }

  .item-name {
    .grid-row(2);
    .grid-column(2);
    margin: auto;
    max-width: 200px;
    white-space: nowrap;
    text-overflow: ellipsis;
    overflow-x: hidden;
    color: @titleColor;
    font-weight: bold;
  }

  &.expanded {
    .grid-template-rows(30px 10px 10px 5px min-content 40px);
    .grid-template-columns(20px min-content auto 35px);
    width: 100%;

    .details-container {
      .grid-row-span(4, 7);
      .grid-column(3);
      .grid;
      margin: auto 0;
      .grid-template-rows(
        20px 10px min-content 10px min-content 10px min-content 15px
      );

      .base-price,
      .item-id,
      .dimensions,
      .description {
        display: flex;
        align-content: center;
        justify-content: center;
        text-align: center;
        padding: 0 15px;
        color: @textColor;
        font-size: 14px;
      }
      .base-price {
        .grid-row(1);
      }

      .item-id {
        .grid-row(3);
      }

      .dimensions {
        .grid-row(5);
      }

      .description {
        .grid-row(7);
      }
    }

    .item-name {
      .grid-column(3);
      .grid-row-span(2, 2);
      max-width: 100%;
    }

    .icon {
      .grid-row-span(3, 7);
      .grid-column(2);

      &:hover {
        cursor: default;
      }
    }

    .icon-close {
      .grid-row-span(1, 3);
      .grid-column(4);
      height: 25px;
      width: 25px;
      margin: auto;
      opacity: 0.5;

      &:hover {
        opacity: 0.8;
      }
    }
  }

  &:hover {
    border: 2px solid @itemBorderHover;
  }
}
</style>
