<script>
import { store } from '../assets/data/store'
export default {
    name: 'MovieCard',
    data: () => ({ store }),
    props: { seriesList: Array, film: Object },
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
    <li>
        <p>{{ film.title }}</p>
        <p>{{ film.original_title }}</p>
        <div :class="film.original_language">{{ getLanguage(film.original_language) }}</div>
        <p>{{ film.vote_average }}</p>
    </li>
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