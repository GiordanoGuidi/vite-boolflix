<script>
import axios from 'axios';
let endpoint = 'https://api.themoviedb.org/3/search/movie'
const apiKey = '7249f678989f4c79f893149db00b1c9f'
import AppHeader from './components/AppHeader.vue';
import SearchForm from './components/SearchForm.vue';
export default {
  name: 'App',
  data: () => ({
    filteredFilms: []
  }),

  components: { AppHeader, SearchForm },
  methods: {
    fetchFilms($event) {
      const url = `${endpoint}?query=${$event}&api_key=${apiKey}`
      axios.get(url).then(res => {
        this.filteredFilms = res.data.results
        console.log(this.filteredFilms)
      })
    }
  }
}
</script>

<template>
  <AppHeader @searched-movie="fetchFilms" />
</template>

<style>
/*CSS RESET*/
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
</style>
