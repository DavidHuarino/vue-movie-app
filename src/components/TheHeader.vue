<template>
    <div class="container wrapper">
        <img src="" alt="">
        <search />
    </div>
</template>
<script>
import Search from '@/components/Search.vue'
export default {
    name: 'TheHeader',
    components: {
        Search
    }
}
</script>
<style lang="scss" scoped>
.container {
    background: red;
    height: 4rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
</style>
