<template>
  <div id="app">
    <!-- <div class="btn-wrap">
      <el-button @click="showTableDemo = !showTableDemo">展示表格</el-button>
      <el-button @click="showCityDemo = !showCityDemo">展示城市组件</el-button>
      <el-button @click="showUserDemo = !showUserDemo">展示用户组件</el-button>
      <el-button @click="showImgCompressDemo = !showImgCompressDemo"
        >展示图片压缩组件</el-button
      >
      <el-button @click="showQRcodeReader = !showQRcodeReader"
        >展示二维码识别</el-button
      >
      <el-button @click="showWordComment = !showWordComment"
        >展示划词高亮</el-button
      >
      <el-button @click="showFileDownload = !showFileDownload"
        >文件下载</el-button
      >
      <el-button @click="showFileStreamDownload = !showFileStreamDownload"
        >流式文件下载</el-button
      >
    </div>
    <div class="demo-block">
      <HelloWorld v-if="showTableDemo" />
      <city-demo v-if="showCityDemo" />
      <el-input-number v-if="showUserDemo" v-model="amount" />
      <user-demo v-if="showUserDemo" :amount="amount" />
      <img-compress-demo v-if="showImgCompressDemo" />
      <QRcodeReader v-if="showQRcodeReader" />
      <WordComment v-if="showWordComment" />
      <FileDowload v-if="showFileDownload" />
      <EleTable v-if="showTableScroll" />
      <FileStreamDownload v-if="showFileStreamDownload" />
    </div> -->

    <el-row class="demo-block" :gutter="12">
      <el-col
        v-for="card in demos"
        :key="card.name"
        :span="card.show ? 24 : 8"
        class="box-item"
      >
        <el-card shadow="hover" class="box-card">
          <div slot="header" class="clearfix">
            <span>{{ card.title }}</span>
            <el-button
              type="text"
              @click="toggleCard(card)"
              style="float: right; padding: 3px 0"
              >展开/收起</el-button
            >
          </div>
          <keep-alive>
            <component v-if="card.show" :is="card.component" />
          </keep-alive>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
// import { templateHtml } from "./utils/utils";
import HelloWorld from "./components/HelloWorld";
import CityDemo from "./components/city-demo";
import UserDemo from "./components/user";
import ImgCompressDemo from "./components/img-compress";
import QRcodeReader from "./components/qrcode-reader";
// import WordComment from "./components/word-comment";
import FileDowload from "./components/file-download";
import EleTable from "./components/ele-table";
import FileStreamDownload from "./components/file-stream-download";
import ImgContent from "./components/imgcontent";
import ImgContent2 from "./components/imgcontent2";
import ParagraphEllipsis from "./components/paragraph-ellipsis";
import IKeepAlive from "./components/i-keep-alive";
import IProvideInject from "./components/i-provide-inject";

export default {
  name: "App",
  components: {
    HelloWorld,
    CityDemo,
    UserDemo,
    ImgCompressDemo,
    QRcodeReader,
    // WordComment,
    FileDowload,
    EleTable,
    FileStreamDownload,
    ImgContent,
    ImgContent2,
    ParagraphEllipsis,
    IKeepAlive,
    IProvideInject,
  },
  data() {
    return {
      showTableDemo: false,
      showCityDemo: false,
      showUserDemo: false,
      showImgCompressDemo: false,
      showQRcodeReader: false,
      showWordComment: false,
      showFileDownload: false,
      showTableScroll: false,
      showFileStreamDownload: false,
      amount: 0,
      demos: [
        {
          name: "HelloWorld",
          title: "表格demo",
          show: false,
          component: "HelloWorld",
        },
        {
          name: "CityDemo",
          title: "城市组件",
          show: false,
          component: "CityDemo",
        },
        {
          name: "UserDemo",
          title: "用户组件",
          show: false,
          component: "UserDemo",
        },
        {
          name: "ImgCompressDemo",
          title: "图片压缩组件",
          show: false,
          component: "ImgCompressDemo",
        },
        {
          name: "QRcodeReader",
          title: "二维码识别",
          show: false,
          component: "QRcodeReader",
        },
        // {
        //   name: "WordComment",
        //   title: "划词高亮",
        //   show: false,
        //   component: "WordComment",
        // },
        {
          name: "FileDowload",
          title: "文件下载",
          show: false,
          component: "FileDowload",
        },
        {
          name: "EleTable",
          title: "表格滚动",
          show: false,
          component: "EleTable",
        },
        {
          name: "FileStreamDownload",
          title: "流式文件下载",
          show: false,
          component: "FileStreamDownload",
        },
        {
          name: "ImgContent",
          title: "图片内容",
          show: false,
          component: "ImgContent",
        },
        {
          name: "ImgContent2",
          title: "图片内容2",
          show: false,
          component: "ImgContent2",
        },
        {
          name: "ParagraphEllipsis",
          title: "文字省略",
          show: false,
          component: "ParagraphEllipsis",
        },
        {
          name: "IKeepAlive",
          title: "缓存组件",
          show: false,
          component: "IKeepAlive",
        },
        {
          name: "IProvideInject",
          title: "provide/inject Demo",
          show: false,
          component: "IProvideInject",
        },
      ],
    };
  },
  watch: {
    showUserDemo(value) {
      if (value) {
        this.changeAmount();
      }
    },
  },
  created() {
    // templateHtml();
  },
  methods: {
    changeAmount() {
      setTimeout(() => {
        this.amount += 1;
      }, 500);
    },
    toggleCard(card) {
      card.show = !card.show;
    },
  },
};
</script>

<style lang="scss" scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}

.demo-block {
  display: flex;
  flex-wrap: wrap;
  .box-item {
    margin-top: 12px;
  }
}

.box-card {
  .text {
    font-size: 14px;
  }
  .clearfix:before,
  .clearfix:after {
    display: table;
    content: "";
  }
  .clearfix:after {
    clear: both;
  }
}
</style>
