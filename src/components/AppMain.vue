<script>
import MovieList from './MovieList.vue';
import MovieCard from './MovieCard.vue';

export default {
    name: 'AppMain',
    components: { MovieList, MovieCard },
    props: { filmList: Array, seriesList: Array },
}

</script>

<template>
    <main>
        <h1>Film</h1>
        <MovieList :filmList="filmList" />

    </main>
</template>

<style></style>