<template>
    <div class="wrapper-search">
        <input type="search" placeholder="search movie" v-model="searchMovies" class="input-search">
        <search-dropdown v-show="movies" :movies="movies" />
    </div>
</template>
<script>
import { ref, watchEffect } from 'vue'
import SearchDropdown from '@/components/SearchDropdown.vue'
export default {
    name: 'Search',
    components: {
        SearchDropdown
    },
    setup() {
        const searchMovies = ref('');
        const movies = ref([]);
        const getSearchMovies = async(search) => {
            const fetchUrl = `https://api.themoviedb.org/3/search/movie?api_key=9a22b0050e2d46e11611865134b2efac&language=en-US&query=${search}&page=1&include_adult=false`;
            const response = await fetch(fetchUrl);
            const data = await response.json();
            movies.value = data.results;
            //console.log(data);
            
        };
        // watchEffect(() => getSearchMovies(searchMovies.value));
        watchEffect(() => {
            if (searchMovies.value) {
                getSearchMovies(searchMovies.value);
            } else {
                movies.value = [];
            }
        });
        // const searchMovie = computed({
        //     get: () => searchMovies,
        //     set: (val) => searchMovies.value = val
        // });
        return {
            searchMovies,
            getSearchMovies,
            movies,
        }
    }
}
</script>
<style lang="scss" scoped>
.wrapper-search {
    display: flex;
    flex-direction: column;
    position: relative;
}
.input-search {
    padding: .5rem .7rem;
    outline: none;
    border: none;
    border-radius: .5rem;
    font-size: .9rem;
}
</style>