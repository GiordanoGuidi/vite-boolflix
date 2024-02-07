<script>
import MovieList from './MovieList.vue';
import MovieCard from './MovieCard.vue';

export default {
    name: 'AppMain',
    components: { MovieList, MovieCard },
    props: { filmList: Array },
}

</script>

<template>
    <main>
        <MovieList :filmList="filmList" />

    </main>
</template>

<style></style>