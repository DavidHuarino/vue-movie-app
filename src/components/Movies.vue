<template>
    <div class="wrapper">
        Vue movie
        <!-- {{ movies }} -->
        <div v-for="(movie, index) in movies" :key="index">
            <img :src="`https://image.tmdb.org/t/p/w500${movie.backdrop_path}`" alt="">
        </div>
    </div>
</template>
<script>
import { ref, onMounted } from 'vue'
export default {
    name: 'Movies',
    setup() {
        const movies = ref([]);
        const fetchUrl = 'https://api.themoviedb.org/3/movie/popular?api_key=9a22b0050e2d46e11611865134b2efac';
        const getMovies = async () => {
            const response = await fetch(fetchUrl);
            const data = await response.json();
            movies.value = data.results;
        }
        onMounted(() => {
            getMovies();
        }); 
        return { fetchUrl, getMovies, movies };
    }
}
</script>