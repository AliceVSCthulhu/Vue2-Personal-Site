<template>
    <i class="iconfont icon-container" :class="curIconName"></i>
</template>

<script>
import iconNames from "./iconName.js"
export default {
    name: "Icon",
    props: {
        type: {
            type: String,
            required: true
        }
    },
    computed: {
        curIconName() {
            return iconNames[this.type]
        }
    }
}
</script>

<style lang="less" scoped>
@import "//at.alicdn.com/t/c/font_5149747_y8tb1ucuiki.css";

.iconfont {
    font-size: inherit;
    color: inherit;
}
</style>