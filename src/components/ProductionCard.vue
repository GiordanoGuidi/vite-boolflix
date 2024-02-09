<script>
import { store } from '../assets/data/store'
export default {
    name: 'ProductionCard',
    data: () => ({
        store, baseUri: 'https://image.tmdb.org/t/p/w342'

    }),
    props: { seriesList: Array, production: Object },
    methods: {
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
        },
        //LINGUA ORIGINALE 
        lang() {
            return this.production.original_language

        },

        //CONTROLLIAMO SE FLAG INCLUDE LE LINGUE DELLE BANDIERE
        hasFlag() {
            const flags = ['it', 'en']
            return flags.includes(this.production.original_language);
        },

        // GENERATO URL COMPLETO DINAMICAMENTE
        flagSrc() {
            const url = new URL(`../assets/img/${this.lang}.png`, import.meta.url)
            return url.href
        }
    }


}
</script>

<template>
    <!--production-card-->
    <!-- <ul class="production-card  list-unstyled">
        <li> -->
    <!-- <p>{{ production.title || production.name }}</p>
            <p>{{ production.original_title || production.original_name }}</p>
            <img class="flag" v-if="hasFlag" :src="flagSrc" :alt="lang">
            <span v-else>{{ lang }}</span>
            <p>{{ this.voteRounded }}</p>
            <p><i class="fa-solid fa-star text-warning"></i><i class="fa-solid fa-star"></i><i
                    class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i></p> -->
    <!-- <img :src="getUrlImage(production)" :alt="production.title">
        </li>
    </ul> -->


    <div class="production-card  list-unstyled" :style="{ backgroundImage: `url(${getUrlImage(production)})` }">
        <p>{{ production.title || production.name }}</p>
        <p>{{ production.original_title || production.original_name }}</p>
        <img class="flag" v-if="hasFlag" :src="flagSrc" :alt="lang">
        <span v-else>{{ lang }}</span>
        <p>{{ this.voteRounded }}</p>
        <p><i v-for="n in 5" class="fa-solid fa-star" :class="n <= this.voteRounded ? 'text-warning' : 'fas'"></i></p>
    </div>
</template>

<style lang="scss" scoped>
@use '../assets/scss/style.scss'
</style>
