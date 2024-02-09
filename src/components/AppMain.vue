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
    <main class="text-white">
        <!--MOVIE-->
        <section id="movie">
            <h2>Film</h2>
            <div class="row card-container row-cols-2 row-cols-md-3 row-cols-lg-5">
                <div class="col" v-for="film in store.films" :key="film.id">
                    <ProductionCard :production="film" />

                </div>
            </div>
            <!--SERIES-->
        </section>
        <section id="series">
            <h2>Series</h2>
            <div class="row card-container row-cols-2 row-cols-md-3 row-cols-lg-5 ">
                <div class="col" v-for="serie in store.series" :key="serie.id">
                    <ProductionCard :production="serie" />
                </div>
            </div>
        </section>
    </main>
</template>

<style lang="scss" scoped>
@use '../assets/scss/style.scss'
</style>