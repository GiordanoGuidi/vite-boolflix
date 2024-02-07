<script>
import SearchForm from './SearchForm.vue'
export default {
    name: 'AppHeader',
    components: { SearchForm }
}

</script>

<template>
    <header class="d-flex align-items-center justify-content-between">
        <h1 class="text-danger">BOOLFIX</h1>
        <SearchForm />
    </header>
</template>

<style>
header {
    height: 150px;
    background-color: black;
    width: 100%;
}
</style>