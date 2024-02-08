<script>
import { store } from '../assets/data/store'
import MovieCard from './MovieCard.vue';
export default {
    name: 'MovieList',
    data: () => ({ store }),

    components: { MovieCard, },
    props: { seriesList: Array },
}

</script>

<template>
    <ul v-for="film in store.films" class="movie-list">
        <MovieCard :film="film" />
    </ul>
</template>

<style></style>