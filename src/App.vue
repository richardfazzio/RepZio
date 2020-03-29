<template>
  <div class="main">
    <Header :company="companyData"></Header>
    <Items :items="items"></Items>
  </div>
</template>

<script>
// Mock data
import data from './assets/data/data.json';

// Components
import Header from './components/Header.vue';
import Items from './components/Items.vue';
export default {
  name: 'App',
  components: {
    Header,
    Items
  },
  data: function () {
    return  {
      items: [],
      companyData: {}
    }
  },
  created: function () {
    // Set icon Url and showMoreData for each item
    data.items.forEach(item => {
      item.icon = `http://images.repzio.com/productimages/${item.ManufacturerID}/logo${item.ManufacturerID}_lg.jpg?w=200&h=200&mode=stretch`;
      item.showMoreData = false;
    });
    this.items = data.items;
    this.companyData = {
      message: data.Message,
      name: data.CompanyName,
      companyLogo: `http://images.repzio.com/productimages/${data.ManufacturerID}/logo${data.ManufacturerID}_lg.jpg?height=100&width=100`
    };
  }
}
</script>
<style lang="less">
@import './assets/less/grid.less';

body {
  margin: 0;
  font-family: sans-serif;
  overflow-y: hidden;
  overflow-x: auto;
}

.main {
  .grid;
  .grid-template-rows(5px auto auto 30px);
  min-width: 450px;

  .header {
    .grid-row(2);
    padding: 0 30px;
  }

  .items {
    .grid-row(3);
    padding: 20px 30px;
  }
}
</style>