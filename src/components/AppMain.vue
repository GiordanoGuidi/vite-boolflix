<script>
import ProductionCard from './ProductionCard.vue'
import { store } from '../assets/data/store'


export default {
    name: 'AppMain',
    data: () => ({ store }),
    components: { ProductionCard, ProductionCard, },
    props: { filmList: Array, seriesList: Array },
}

</script>

<template>
    <main>
        <h1>Film</h1>
        <ProductionCard v-for="film in store.films" :key="film.id" :production="film" />
        <h1>Series</h1>
        <ProductionCard v-for="serie in store.series" :key="serie.id" :production="serie" />

    </main>
</template>

<style></style>