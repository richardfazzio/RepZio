<!-- Main Component -->
<template>
  <div class="header">
    <div class="content">
      <img class="company-logo" :src="company.companyLogo" />
      <div class="company-name">{{ company.name }}</div>
      <div class="message" v-html="company.message"></div>
    </div>
    <div class="border"></div>
  </div>
</template>
<script>
export default {
  name: "Header",
  props: {
    company: Object
  },
  created: function() {
    console.log("company", this.company);
  }
};
</script>
<style lang="less">
@import "../assets/less/grid.less";
@import "../assets/less/colors.less";

.header {
  .content {
    .grid;
    .grid-template-rows(20px 40px min-content auto auto 20px);
    .grid-template-columns(20px min-content 10px auto);

    .company-logo {
      .grid-row-span(2, 2);
      .grid-column(2);
      margin: auto;
    }

    .company-name,
    .message {
      .grid-column(4);
    }

    .company-name {
      .grid-row(2);
      display: flex;
      align-content: center;
      justify-content: center;
      color: @titleColor;
      font-size: 30px;
    }

    .message {
      .grid-row(3);
      padding-top: 20px;
      margin: 0 auto;
      max-width: 100%;
      text-overflow: break-word;
      text-align: center;
      font-size: 20px;
      color: @textColor;

      > p {
        display: inline;
        padding-top: 10px;
        margin: 0;
        text-align: center;
      }
    }
  }

  .border {
    width: 100%;
    border-bottom: 1px solid @border;
  }
}
</style>
