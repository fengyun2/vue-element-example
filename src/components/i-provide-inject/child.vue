<template>
  <div class="page">
    <h4>child</h4>
    <p>不可响应的数据--msg: {{ msg }}</p>
    <p>可响应的数据--activeData: {{ activeData.msg || "" }}</p>
    <el-button @click="printDetail">打印</el-button>
    <p>来自父级的内容--text: {{ detailVm.text }}</p>
  </div>
</template>

<script>
export default {
  name: "child",
  inject: ["msg", "activeData", "detailVm"],
  mounted() {
    console.log("child mounted");
  },
  methods: {
    printDetail() {
      console.log(this.detailVm.text); // 获取detail中的变量;
      this.detailVm.text = "对不起我在子组件中修改了";
      this.detailVm.say(); // 调用detail中的方法;
    },
  },
};
</script>

<style></style>
