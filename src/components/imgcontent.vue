<template>
  <div class="demo">
    <el-button @click="getContents">转换代码</el-button>
    <div class="content" v-html="content"></div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      content: "",
    };
  },
  methods: {
    getContents() {
      const content = `
            <p><img width="100%" height="100%" src="https://i.ibb.co/646433X/image.png" alt="image"><span>我是大图，需要装</span><img width="100%" height="100%" src="https://i.ibb.co/646433X/image.png" alt="image"><img width="100%" height="100%" src="https://i.ibb.co/646433X/image.png" alt="image"><span>我是大图，需要装</span></p>
            `;

      const convertedContent = content.replace(
        /<img (width="100%" height="100%") src="(.*?)" alt="(.*?)">/g,
        `<el-image
            style="$1"
            :src="$2"
            :preview-src-list="[$2]">
            </el-image>`
      );
      this.content = convertedContent;
    },
  },
};
</script>
