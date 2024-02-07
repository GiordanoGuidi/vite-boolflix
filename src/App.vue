<script>
import axios from 'axios';
let endpoint = 'https://api.themoviedb.org/3/search/movie';
const apiKey = '7249f678989f4c79f893149db00b1c9f'
import AppHeader from './components/AppHeader.vue'
import SearchForm from './components/SearchForm.vue'
import AppMain from './components/AppMain.vue'
import { store } from './assets/data/store'
import MovieList from './components/MovieList.vue'
import MovieCard from './components/MovieCard.vue';

export default {
  name: 'App',
  data: () => ({
    filteredFilms: []
  }),

  components: { AppHeader, SearchForm, AppMain, MovieList, MovieCard },
  methods: {
    // METODO CHE FILTRA I FILM
    fetchFilms($event) {
      const url = `${endpoint}?query=${$event}&api_key=${apiKey}`
      axios.get(url).then(res => {
        this.filteredFilms = res.data.results
        // store.films = res.data.results
      })
    }
  }
}
</script>

<template>
  <!--HEADER-->
  <AppHeader @searched-movie="fetchFilms" />
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
