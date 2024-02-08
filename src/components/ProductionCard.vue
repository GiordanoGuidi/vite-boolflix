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
        },
        /*FUNZIONE CHE CREA URL SE NELL'API C'E' L'IMMAGINE
        ALTRIMENTI METTE UN IMMAGINE DEFAULT*/
        getUrlImage(production) {
            const apiImage = `${this.baseUri}${this.production.poster_path} `
            const defaultImage = 'https://www.shutterstock.com/image-vector/collection-blank-cinema-film-strip-260nw-184250981.jpg'
            if (production.poster_path) {
                return apiImage
            } else {
                return defaultImage
            }
        },

    },

    computed: {
        //VOTO DIVISO PER DUE E ARROTONDATO X ECCESSO
        voteRounded() {
            const vote = this.production.vote_average;
            const voteRounded = Math.round(vote / 2)
            return voteRounded

        }
    }


}

</script>

<template>
    <!--production-card-->
    <ul class="production-card">
        <li>
            <p>{{ production.title || production.name }}</p>
            <p>{{ production.original_title || production.original_name }}</p>
            <div :class="production.original_language">{{ getLanguage(production.original_language) }}</div>
            <p>{{ this.voteRounded }}</p>
            <img :src="getUrlImage(production)" :alt="production.title">
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