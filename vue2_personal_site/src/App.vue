<template>
  <div>
    <Avatar url="https://img1.baidu.com/it/u=2659077985,44740634&fm=253&fmt=auto&app=120&f=JPEG?w=889&h=500" />
    <Icon type="weixin" />
    <Pager :total="822" :current="current" @pageChange="handlePageChange" />
    <div class="test">
      <Empty :text="text" />
    </div>
  </div>
</template>

<script>
import Avatar from './components/Avatar';
import Icon from "./components/Icon";
import Pager from "./components/Pager";
import Empty from "./components/Empty";
export default {
  components: {
    Avatar,
    Icon,
    Pager,
    Empty,
  },
  data() {
    return {
      current: 1,
      // empty
      text: "无数据",
    }
  },
  methods: {
    handlePageChange(val) {
      this.current = val;
    }
  }
}
</script>

<style lang="less" scoped></style>