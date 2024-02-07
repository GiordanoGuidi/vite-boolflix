<script>
// import { store } from '../assets/data/store';
import MovieCard from './MovieCard.vue';
export default {
    name: 'MovieList',
    components: { MovieCard, },
    props: { filmList: Array },
}

</script>

<template>
    <main>
        <ul>
            <MovieCard :filmList="filmList" />
        </ul>
    </main>
</template>

<style></style>