<template>
  <div class="page">
    <h3>keep-alive demo</h3>
    <el-tabs style="margin-top: 15px" v-model="activeName">
      <el-tab-pane
        v-for="tab in tabs"
        :key="tab.name"
        :name="tab.name"
        :label="tab.label"
      >
      </el-tab-pane>
    </el-tabs>

    <keep-alive>
      <component :is="activeName" />
    </keep-alive>
  </div>
</template>

<script>
import Child1 from "./child1";
import Child2 from "./child2";
export default {
  name: "i-keep-alive",
  components: {
    Child1,
    Child2,
  },
  data() {
    return {
      activeName: "child1",
      cache: {},
      tabs: [
        {
          name: "child1",
          label: "child1",
          component: "Child1",
        },
        {
          name: "child2",
          label: "child2",
          component: "Child2",
        },
      ],
    };
  },
  methods: {},
};
</script>

<style></style>
