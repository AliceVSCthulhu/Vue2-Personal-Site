<template>
  <div>
    <Pager :total="822" :current="current" @pageChange="handlePageChange" />
  </div>
</template>

<script>
import Pager from "./index.vue"
export default {
  components: {
    Pager,
  },
  data() {
    return {
      current: 1,
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