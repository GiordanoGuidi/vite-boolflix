<script>
import { store } from '../assets/data/store'
export default {
    name: 'ProductionCard',
    data: () => ({
        store, baseUri: 'https://image.tmdb.org/t/p/w342'

    }),
    props: { seriesList: Array, production: Object },
    methods: {
        getLanguage(language) {
            if (language === 'en' || language === 'it') {
                return
            } else {
                return language
            }
        }
    },
}

</script>

<template>
    <ul class="movie-card">
        <li>
            <p>{{ production.title || production.name }}</p>
            <p>{{ production.original_title || production.original_name }}</p>
            <div :class="production.original_language">{{ getLanguage(production.original_language) }}</div>
            <p>{{ production.vote_average }}</p>
            <img :src="`${baseUri}${production.poster_path} `" :alt="production.title">
        </li>
    </ul>
</template>

<style>
.en {
    background-image: url(../assets/img/en.png);
    background-position: center;
    background-size: cover;
    margin-bottom: 10px;
    height: 30px;
    width: 50px;
}

.it {
    background-image: url(../assets/img/it.png);
    background-position: center;
    background-size: cover;
    height: 30px;
    width: 50px;
    margin-bottom: 10px;

}
</style>