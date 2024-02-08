<script>
import SearchForm from './SearchForm.vue'
export default {
    name: 'AppHeader',
    components: { SearchForm },
    emits: ['searched-movie'],
}

</script>

<template>
    <!--HEADER-->
    <header class="d-flex align-items-center justify-content-between">
        <h1 class="text-danger">BOOLFIX</h1>
        <!--FORM-->
        <SearchForm @input-text="$emit('searched-movie', $event)" buttonLabel="Cerca" placeholder="Cerca Film o Serie" />
    </header>
</template>

<style>
header {
    height: 150px;
    background-color: black;
    width: 100%;
}
</style>