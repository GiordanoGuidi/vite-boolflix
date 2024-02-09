<script>
import { store } from '../assets/data/store';
import { api, imgApi } from '../assets/data/index';

export default {
    name: 'ProductionCard',
    data: () => ({
        store,
    }),
    props: { seriesList: Array, production: Object },
    methods: {
        /*FUNZIONE CHE CREA URL SE NELL'API C'E' L'IMMAGINE
        ALTRIMENTI METTE UN IMMAGINE DEFAULT*/
        getUrlImage(production) {
            const apiImage = `${imgApi.baseUri}${production.poster_path} `
            if (production.poster_path) {
                return apiImage
            } else {
                return imgApi.default
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
    <ul class="production-card  list-unstyled">
        <li v-show="production.title">
            <p>{{ production.title }}</p>
            <p v-if="production.title !== production.original_title">
                {{ production.original_title }}</p>
        </li>
        <li v-show="production.name">
            <p>{{ production.name }}</p>
            <p v-if="production.name !== production.original_name">
                {{ production.original_name }}</p>
        </li>
        <li>
            <img class="flag" v-if="hasFlag" :src="flagSrc" :alt="lang">
            <span v-else>{{ lang }}</span>
        </li>

        <li>
            <p>{{ this.voteRounded }}</p>
        </li>
        <li class="pippo">
            <img :src="getUrlImage(production)" :alt="production.title" class="production-img img-fluid">
        </li>
        <li>
            <p><i v-for="n in 5" class="fa-solid fa-star" :class="n <= this.voteRounded ? 'text-warning' : 'fas'"></i></p>
        </li>
    </ul>
</template>

<style lang="scss" scoped>
@use '../assets/scss/style.scss'
</style>
