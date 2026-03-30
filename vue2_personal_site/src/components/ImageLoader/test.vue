<template>
    <div class="test">
        <ImageLoader :src="src" :placeholder="placeholder" @load="handleLoad" :duration="duration" />
    </div>
</template>

<script>
import ImageLoader from "./index.vue";
export default {
    components: {
        ImageLoader,
    },
    data() {
        return {
            src: "https://images.pexels.com/photos/33109/fall-autumn-red-season.jpg?fit=crop&crop=entropy&w=3456&h=2304",
            placeholder: "https://images.pexels.com/photos/33109/fall-autumn-red-season.jpg?w=100",
            duration: 5000,
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