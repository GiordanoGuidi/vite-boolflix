<script>
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import SearchForm from './components/SearchForm.vue';
export default {
  name: 'App',

  components: { AppHeader, SearchForm }
}
</script>

<template>
  <AppHeader />
</template>

<style>
/*CSS RESET*/
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
</style>
