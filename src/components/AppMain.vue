<script>
import ProductionCard from './ProductionCard.vue';
import { store } from '../assets/data/store'


export default {
    name: 'AppMain',
    data: () => ({ store }),
    components: { ProductionCard, ProductionCard, ProductionCard },
    props: { filmList: Array, seriesList: Array },
}

</script>

<template>
    <main>
        <h1>Film</h1>
        <ProductionCard v-for="film in store.films" :production="film" />
        <h1>serie</h1>
        <ProductionCard v-for="serie in store.series" :production="serie" />

    </main>
</template>

<style></style>