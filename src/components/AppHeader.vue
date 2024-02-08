<script>
import SearchForm from './SearchForm.vue'
export default {
    name: 'AppHeader',
    components: { SearchForm },
    emits: ['searched-movie'],
}

</script>

<template>
    <header class="d-flex align-items-center justify-content-between">
        <h1 class="text-danger">BOOLFIX</h1>
        <!--FORM-->
        <SearchForm @input-text="$emit('searched-movie', $event)" buttonLabel="Cerca" placeholder="Cerca Film o Serie" />
    </header>
</template>

<style lang="scss" scoped>
@use '../assets/scss/style.scss'
</style>