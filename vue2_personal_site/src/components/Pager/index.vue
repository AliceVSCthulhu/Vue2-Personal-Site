<template>
  <div class="pager-container">
    <span :style="{ cursor: isFirstPage ? 'not-allowed' : 'pointer' }" @click="handleClick($event, 1)">首页</span>
    <span :style="{ cursor: isFirstPage ? 'not-allowed' : 'pointer' }"
      @click="handleClick($event, current - 1)">上一页</span>
    <span v-for="(page, index) in visiblePages" :key="index" :class="{ active: page === current }"
      @click="handleClick($event, page)">第{{ page }}页</span>
    <span :style="{ cursor: isLastPage ? 'not-allowed' : 'pointer' }"
      @click="handleClick($event, current + 1)">下一页</span>
    <span :style="{ cursor: isLastPage ? 'not-allowed' : 'pointer' }" @click="handleClick($event, totalPage)">尾页</span>
    <span style="margin-right: 0;">转到</span>
    <select @change="handleClick($event)">
      <option selected>...</option>
      <option v-for="(i, index) in totalPageArr" :key="index" :value="i" class="select">{{ i }}</option>
    </select>
    <span>页</span>
  </div>
</template>

<script>
export default {
  name: "Pager",
  props: {
    current: {
      // 当前页
      type: Number,
      default: 1,
    },
    total: {
      // 总数据量
      type: Number,
      default: 0,
    },
    limit: {
      // 页容量
      type: Number,
      default: 10,
    },
    visibleNumber: {
      // 可见页码数
      type: Number,
      default: 10,
    },
  },
  computed: {
    totalPage() {
      // 总页数
      return Math.ceil(this.total / this.limit);
    },
    visibleFirstPage() {
      //可见区第一页页码
      const minNum = this.current - Math.floor(this.visibleNumber / 2);
      if (minNum <= 0) {
        return 1;
      } else {
        return minNum;
      }
    },
    visibleLastPage() {
      //可见区最后一页页码
      const maxNum = this.current + this.visibleNumber - Math.floor(this.visibleNumber / 2) - 1;
      if (maxNum > this.totalPage) {
        return this.totalPage;
      } else {
        return maxNum;
      }
    },
    visiblePages() {
      const pages = [];
      for (let i = this.visibleFirstPage; i <= this.visibleLastPage; i++) {
        pages.push(i);
      }
      return pages;
    },
    isFirstPage() {
      // 处理首页、上一页鼠标悬停效果显示
      return this.current === 1;
    },
    isLastPage() {
      //处理尾页、下一页鼠标悬停效果显示
      return this.current === this.totalPage;
    },
    totalPageArr() {
      const arr = [];
      for (let i = 1; i <= this.totalPage; i++) {
        arr.push(i);
      }
      return arr;
    }
  },
  methods: {
    handleClick(e, val) {
      let value;
      if (e.target.value) {
        value = Number(e.target.value);
      } else {
        value = val;
      }
      //设置范围
      if (value < 1 || value > this.totalPage) {
        return;
      }
      this.$emit('pageChange', value);
    }
  },
}
</script>

<style lang="less" scoped>
.pager-container {
  span {
    margin-right: 15px;
    cursor: pointer;

    &:last-child {
      margin-right: 0
    }

    &.active {
      font-weight: bold;
    }
  }
}
</style>