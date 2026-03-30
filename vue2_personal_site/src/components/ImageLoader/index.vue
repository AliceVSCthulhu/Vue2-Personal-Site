<template>
    <div class="imageLoader-container">
        <img class="main" :src="src" @load="handleTransitionEnd">
        <img v-if="shouldShow" class="placeholder"
            :style="{ opacity: placeholderOpacity, transition: `opacity ${duration}ms ease` }" :src="placeholder">
    </div>
</template>

<script>
export default {
    name: "ImageLoader",
    data() {
        return {
            shouldShow: true,
            originLoaded: false,
        }
    },
    props: {
        src: {
            type: String,
            required: true,
        },
        placeholder: {
            type: String,
            required: true,
        },
        duration: {
            type: Number,
            default: 500,
        }
    },
    methods: {
        handleTransitionEnd() {
            // 原图加载完成
            this.originLoaded = true;
            setTimeout(() => {
                // 等待过渡完成
                this.shouldShow = false;
                this.$emit("load");
            }, this.duration);
        }
    },
    computed: {
        placeholderOpacity() {
            return this.originLoaded ? 0 : 1;
        }
    }
}
</script>

<style lang="less" scoped>
.imageLoader-container {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100%;
    position: relative;

    img {
        position: absolute;
        width: 100%;
        height: 100%;

        &.main {
            object-fit: cover;
        }

        &.placeholder {
            z-index: 10;
            filter: blur(20px);
            transform: scale(1.1);
        }
    }
}
</style>