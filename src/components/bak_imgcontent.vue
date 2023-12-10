<script>
const content = `
            <p><img width="100%" height="100%" src="https://cdn.pixabay.com/photo/2014/11/30/14/11/cat-551554_1280.jpg" alt="image"><div style="display: flex; justify-content: center;"><h3 style="text-align: center;">我是大图，需要装</h3><span>我是描述语</span></div><img width="100%" height="100%" src="https://cdn.pixabay.com/photo/2014/11/30/14/11/cat-551554_1280.jpg" alt="image"><div style="display: flex; justify-content: center;"><h3 style="text-align: center;">我是大图，需要装</h3><span>我是描述语</span></div><img width="100%" height="100%" src="https://cdn.pixabay.com/photo/2014/11/30/14/11/cat-551554_1280.jpg" alt="image"><div style="display: flex; justify-content: center;"><h3 style="text-align: center;">我是大图，需要装</h3><span>我是描述语</span></div></p>
            `;
export default {
  data() {
    return {
      content: "",
    };
  },
  mounted() {
    this.getContents();
  },
  methods: {
    // getContents() {
    //   const content = `
    // <p><img width="100%" height="100%" src="https://cdn.pixabay.com/photo/2014/11/30/14/11/cat-551554_1280.jpg" alt="image"><div style="display: flex; justify-content: center;"><h3 style="text-align: center;">我是大图，需要装</h3><span>我是描述语</span></div><img width="100%" height="100%" src="https://cdn.pixabay.com/photo/2014/11/30/14/11/cat-551554_1280.jpg" alt="image"><div style="display: flex; justify-content: center;"><h3 style="text-align: center;">我是大图，需要装</h3><span>我是描述语</span></div><img width="100%" height="100%" src="https://cdn.pixabay.com/photo/2014/11/30/14/11/cat-551554_1280.jpg" alt="image"><div style="display: flex; justify-content: center;"><h3 style="text-align: center;">我是大图，需要装</h3><span>我是描述语</span></div></p>
    // `;

    //   const convertedContent = content.replace(
    //     /<img (width="100%" height="100%") src="(.*?)" alt="(.*?)">/g,
    //     `<el-image
    //         style="$1"
    //         :src="$2"
    //         :preview-src-list="[$2]">
    //         </el-image>`
    //   );
    //   console.log(convertedContent, " convertedContent");
    //   this.content = convertedContent;
    // },

    getContents() {
      this.content = content;
    },

    renderContent(h) {
      // This is a naive implementation using split. For a more robust solution consider using proper HTML parsing.
      const segments = this.content.split(/(<img.*?>)/g);

      return h(
        "div",
        { class: "content" },
        segments.map((segment) => {
          // Test if this is an <img> element.
          const imgMatch = segment.match(
            /<img width="(100%)" height="(100%)" src="(.*?)" alt="(.*?)">/
          );
          if (imgMatch) {
            const [, width, height, src, alt] = imgMatch;
            // return (
            //   <el-image
            //     style={{ width, height }}
            //     src={src}
            //     preview-src-list={[src]}
            //     alt={alt}
            //   />
            // );
            return h("el-image", {
              props: {
                style: { width, height },
                src,
                previewSrcList: [src],
                alt,
              },
            });
          } else {
            // This is not an <img>, render it as-is.
            // return segment;
            return h("div", { domPropsInnerHTML: segment });
          }
        })
      );

      // return segments.map((segment) => {
      //   // Test if this is an <img> element.
      //   const imgMatch = segment.match(
      //     /<img width="(100%)" height="(100%)" src="(.*?)" alt="(.*?)">/
      //   );
      //   if (imgMatch) {
      //     const [, width, height, src, alt] = imgMatch;
      //     return (
      //       <el-image
      //         style={{ width, height }}
      //         src={src}
      //         preview-src-list={[src]}
      //         alt={alt}
      //       />
      //     );
      //   } else {
      //     // This is not an <img>, render it as-is.
      //     return segment;
      //   }
      // });
    },
  },

  render(h) {
    return (
      <div class="demo">
        <el-button onClick="getContents">转换代码</el-button>
        {this.renderContent(h)}
        {/* <div class="content" domPropsInnerHTML={this.renderContent(h)}></div> */}
      </div>
    );
  },
};
</script>
