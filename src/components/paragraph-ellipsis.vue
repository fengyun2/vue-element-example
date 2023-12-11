<template>
  <!-- 超出 3 行展示更多 -->
  <div>
    <div
      class="content"
      :class="{ clamp: !expanded }"
      :style="{ maxHeight: contentHeight }"
    >
      <p>
        从旁边树上坠落下来的两颗小果子，刚开始的时候还以为是两颗小葡萄。这两颗小果子在雨中并没有滚来滚去。反而在雨中显得“格外安静”。
      </p>
      <div class="ne-image-box" style="">
        <img
          width="600"
          class="ne-image ne-image-preview"
          alt="DSC03274.JPG"
          draggable="true"
          :src="require('../assets/DSC03274.jpg')"
        />
      </div>
      <p>
        两片落叶。左侧是红黄色，是先拍到的，之所有想拍，是它在被雨水淋湿后，颜色鲜艳到引起了我的注意。右侧的是在杭州很常见的银杏树叶，在秋天的是时候会是好看的金黄色，可以收集一些来做书签。
        两片树叶除了颜色不一样，一片像是在水中浸泡过湿漉漉的，而另外一片则像是刚下完澡出来，只挂着一些水珠
      </p>
      <div class="ne-image-box" style="">
        <div
          width="340"
          style="max-width: 100%; width: 340px; overflow: hidden"
        >
          <img
            width="600.6666666666666"
            class="ne-image ne-image-preview"
            alt="DSC03208.JPG"
            draggable="true"
            :src="require('../assets/DSC03208.jpg')"
          />
        </div>
      </div>
      <p>
        雨水滴落在马路上。真的就像是大珠小珠落玉盘，所以当时不仅拍了照，还用手机录了视频。
      </p>
      <div class="ne-image-box" style="">
        <img
          width="600"
          class="ne-image ne-image-preview"
          alt="DSC03255.JPG"
          draggable="true"
          :src="require('../assets/DSC03255.jpg')"
        />
      </div>
    </div>
    <button @click="toggle">
      {{ expanded ? "Show Less" : "Show More" }}
    </button>
  </div>
</template>

<script>
export default {
  name: "ParagraphEllipsis",
  data() {
    return {
      expanded: false,
      lineheight: 1.5, // 实际的行高需要根据内容和样式调整
      maxLine: 3, // 最大行数
    };
  },
  computed: {
    contentHeight() {
      // 展开时无最大高度限制
      if (this.expanded) {
        return "none";
      }
      // 折叠时高度为行高乘以最大行数
      return `${this.maxLine * this.lineheight}em`;
    },
  },
  methods: {
    toggle() {
      this.expanded = !this.expanded;
    },
  },
};
</script>

<style scoped>
.content {
  position: relative;
  overflow-y: hidden;
}
.content.clamp p {
  /* display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden; */
}
</style>
