<template>
  <el-table
    v-loading.fullscreen.lock="loading"
    :data="tableData"
    style="width: 100%"
  >
    <el-table-column prop="date" label="日期" width="180"> </el-table-column>
    <el-table-column prop="name" label="姓名" width="180"> </el-table-column>
    <el-table-column prop="address" label="地址"> </el-table-column>
  </el-table>
</template>

<style>
body {
  margin: 0;
}
</style>

<script>
const delay = (time) => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve();
    }, time);
  });
};
export default {
  name: "childItem",
  data() {
    return {
      tableData: [],
      loading: false,
    };
  },
  methods: {
    async fetchData() {
      this.loading = true;
      // 延迟 20s 关闭loading
      await delay(20 * 1000);
      this.loading = false;
      this.tableData = [
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
      ];
    },
  },
  mounted() {
    console.log("childItem mounted");
    this.fetchData();
  },
  activated() {
    console.log("childItem activated");
  },
  deactivated() {
    console.log("childItem deactivated");
  },
};
</script>
