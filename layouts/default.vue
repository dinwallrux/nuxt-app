<template>
  <el-container>
    <Sidebar />
    <el-container direction="vertical">
      <Header />
      <el-main>
        <nuxt/>
      </el-main>
    </el-container>
  </el-container>
</template>

<style>
  .el-header {
    background-color: #B3C0D1;
    color: #333;
    line-height: 60px;
  }
  
  .el-aside {
    color: #333;
  }
</style>

<script>
  import Header from '~/components/partials/Header.vue'
  import Sidebar from '~/components/partials/Sidebar.vue'

  export default {
    components: {
      Header,
      Sidebar
    },
    data() {
      const item = {
        date: '2016-05-02',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      };
      return {
        tableData: Array(20).fill(item)
      }
    }
  };
</script>