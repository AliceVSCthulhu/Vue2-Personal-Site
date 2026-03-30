<template>
  <div>
    <Avatar url="https://img1.baidu.com/it/u=2659077985,44740634&fm=253&fmt=auto&app=120&f=JPEG?w=889&h=500" />
    <Icon type="weixin" />
    <Pager :total="822" :current="current" @pageChange="handlePageChange" />
    <Empty :text="text" />
    <div class="test">
      <ImageLoader :src="src" :placeholder="placeholder" @load="handleLoad" :duration="duration" />
    </div>
  </div>
</template>

<script>
import Avatar from './components/Avatar';
import Icon from "./components/Icon";
import Pager from "./components/Pager";
import Empty from "./components/Empty";
import ImageLoader from "./components/ImageLoader";
export default {
  components: {
    Avatar,
    Icon,
    Pager,
    Empty,
    ImageLoader,
  },
  data() {
    return {
      current: 1,
      // empty
      text: "无数据",
      // ImageLoader
      src: "https://images.pexels.com/photos/33109/fall-autumn-red-season.jpg?fit=crop&crop=entropy&w=3456&h=2304",
      placeholder: "https://images.pexels.com/photos/33109/fall-autumn-red-season.jpg?w=100",
      duration: 1000,
    }
  },
  methods: {
    handlePageChange(val) {
      this.current = val;
    },
    handleLoad() {
      console.log("图片已加载");
    }
  }
}
</script>

<style lang="less" scoped>
.test {
  width: 1366px;
  height: 960px;
}
</style>