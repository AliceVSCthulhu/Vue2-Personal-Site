<template>
    <div class="avatar-container">
        <img :src=url :style="{ width: size + 'px', height: size + 'px' }">
    </div>
</template>

<script>
export default {
    props: {
        url: {
            type: String,
            required: true
        },
        size: {
            type: Number,
            default: 150
        }
    }
}
</script>

<style lang="less" scoped>
.avatar-container {
    img {
        border-radius: 50%;
        object-fit: cover;
    }
}
</style>