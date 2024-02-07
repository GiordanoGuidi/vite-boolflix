<script>
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
export default {
  name: 'App',

  components: { AppHeader }
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
