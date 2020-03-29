<!-- Main Component -->
<template>
  <div class="header">
    <div class="content">
      <img class="company-logo" :src="company.companyLogo" />
      <div class="company-name">{{ company.name }}</div>
      <div class="message" v-html="company.message"></div>
      <div class="sales-rep">
        <div class="description">Sales Representative Information: </div>
        <div class="name"><b>Name</b>: {{ fullName }}</div>
        <div class="location"><b>Location</b>: {{ location }}</div>
        <div class="email">
          Please contact me at
          <a :href="`mailto:${company.SalesRep.EmailAddress}`">{{ company.SalesRep.EmailAddress }}</a>
          or call me at {{ company.SalesRep.Phone }}
        </div>
      </div>
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
  computed: {
    location: function() {
      return `${this.company.SalesRep.City} ${this.company.SalesRep.State}, ${this.company.SalesRep.PostalCode}`;
    },
    fullName: function() {
      return `${this.company.SalesRep.FirstName} ${this.company.SalesRep.LastName}`;
    }
  }
};
</script>
<style lang="less">
@import "../assets/less/grid.less";
@import "../assets/less/colors.less";

.header {
  .content {
    .grid;
    .grid-template-rows(20px 40px min-content auto auto auto 20px);
    .grid-template-columns(20px min-content 10px auto);

    .company-logo {
      .grid-row-span(2, 2);
      .grid-column(2);
      margin: auto;
    }

    .company-name,
    .message,
    .sales-rep {
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
      font-size: 16px;
      color: @textColor;

      > p {
        display: inline;
        padding-top: 10px;
        margin: 0;
        text-align: center;
      }
    }

    .sales-rep {
      .grid-row(4);
      text-align: center;

      .description {
        color: @titleColor;
        font-size: 20px;
        font-weight: bold;
      }

      .name,
      .location,
      .email {
        color: @textColor;
        font-size: 16px;
      }
    }
  }

  .border {
    width: 100%;
    border-bottom: 1px solid @border;
  }
}
</style>
