<template>
  <div class="child2">
    <h3>Child 2</h3>
    <ChildItemVue v-if="show" />
    <!-- <ChildItemVue /> -->
  </div>
</template>

<script>
import ChildItemVue from "./childItem";

const delay = (time) => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve();
    }, time);
  });
};

export default {
  name: "child2",
  components: {
    ChildItemVue,
  },
  data() {
    return {
      show: false,
    };
  },
  mounted() {
    console.log("child2 mounted");
    this.loadData();
  },
  activated() {
    console.log("child2 activated");
  },
  deactivated() {
    console.log("child2 deactivated");
  },
  methods: {
    async loadData() {
      // 延迟 20s 切换show为true,测试keep-alive是否被激活，影响到childItem-loading无法关闭
      await delay(20 * 1000);
      this.$emit("loadData");
      this.show = true;
    },
  },
};
</script>

<style></style>
