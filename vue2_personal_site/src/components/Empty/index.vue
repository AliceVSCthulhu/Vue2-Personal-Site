<template>
    <div class="empty-container">
        <Icon :type="iconType" />
        <span>{{ text }}</span>
    </div>
</template>

<script>
import Icon from "../Icon/index";
export default {
    name: "Empty",
    data() {
        return {
            iconType: "empty",
        }
    },
    components: {
        Icon,
    },
    props: {
        text: {
            type: String,
            default: "无数据",
        }
    }
}
</script>

<style lang="less" scoped>
@color: rgb(175, 175, 175);

.empty-container {
    display: flex;
    width: 100%;
    height: 100%;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: @color;

    .iconfont {
        font-size: 10em;
    }

    span {
        font-size: 1.3em;
        font-family: 'heiti';
    }
}
</style>