<template>
  <div class="page">
    <h3>provide / inject</h3>
    <p>
      <el-input
        v-model="msg"
        placeholder="请输入内容"
        @change="handleChangeMsg"
      ></el-input>
      <Child />
    </p>
  </div>
</template>

<script>
// [你可能不知道的provide / inject 用法](https://segmentfault.com/a/1190000020954324)
import Child from "./child.vue";
export default {
  name: "i-provide-inject",
  components: {
    Child,
  },
  provide() {
    return {
      msg: this.msg,
      activeData: this.activeData,
      detailVm: this, // 传递父级
    };
  },
  data() {
    return {
      msg: "hello world",
      activeData: {
        msg: "hello world",
      },
      text: "say hello",
    };
  },
  methods: {
    handleChangeMsg(value) {
      this.activeData.msg = value;
    },
    say() {
      console.log(this.text);
    },
  },
};
</script>

<style></style>
