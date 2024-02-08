<script>
import axios from 'axios';
import { api } from './assets/data/index'
import AppHeader from './components/AppHeader.vue'
import SearchForm from './components/SearchForm.vue'
import AppMain from './components/AppMain.vue'
import { store } from './assets/data/store'
import ProductionCard from './components/ProductionCard.vue';

export default {
  name: 'App',
  data: () => ({
    filteredFilms: [],
    filteredTvSeries: []
  }),

  components: { AppHeader, SearchForm, AppMain, ProductionCard },
  methods: {
    // FUNZIONE CHE FILTRA I FILM
    fetchFilms($event) {
      const { baseUri, apiKey, language } = api
      const url = `${baseUri}/search/movie?query=${$event}&api_key=${apiKey}&language=${language}`
      axios.get(url)
        .then(res => {
          this.filteredFilms = res.data.results;
          store.films = res.data.results
          console.log('store-film', store.films)
        })
        .catch(err => {
          console.error(err)
        })
    },

    // FUNZIONE CHE FILTRA LE SERIE TV
    fetchTvSeries($event) {
      const { baseUri, apiKey, language } = api
      const url = `${baseUri}/search/tv?api_key=${apiKey}&language=${language}&query=${$event}`;
      axios.get(url)
        .then(res => {
          this.filteredTvSeries = res.data.results
          console.log(this.filteredTvSeries)
          store.series = res.data.results
          console.log('store-series', store.series)
        })
        .catch(err => {
          console.error(err)
        })
    },
    // FUNZIONE CHE RICHIAMA FILTRO DEI FILM E DELLE SERIE
    searchProduction($event) {
      this.fetchFilms($event);
      this.fetchTvSeries($event)
    }
  }
}
</script>

<template>
  <!--HEADER-->
  <AppHeader @searched-movie="searchProduction($event)" />
  <!--MAIN-->
  <AppMain :filmList="filteredFilms" />
</template>

<style>
/*CSS RESET*/
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
</style>
