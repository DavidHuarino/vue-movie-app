<template>
    <div class="search-dropdown">
        <div v-for="(movie, index) in movies" :key="index">
            {{ movie.title }}
        </div>
        <!-- <ul>
            <li v v-for="(movie, index) in movies" :key="index">
                {{ movie.title }}
            </li>
        </ul> -->
    </div>
</template>
<script>
export default {
    name: 'SearchDropdown',
    props: {
        movies: {
            type: Array,
            required: true
        }
    },
    setup() {
        
    }
}
</script>
<style lang="scss" scoped>
.search-dropdown {
    z-index: 100;
    max-height: 20rem;
    width: 100%;
    border-radius: .5rem;
    position: absolute;
    // overflow-y: auto;
    overflow-y: scroll;
    top: 2rem;
    background: #fff;
}
</style>