<script>

export default {
    name: 'SearchForm',

    data: () => ({
        searchText: ''
    }),
    emits: ['input-text']
}

</script>

<template>
    <!--FORM-->
    <form @submit.prevent="$emit('input-text', searchText)" class="d-flex gap-3">
        <input type="text" class="form-control" id="#" v-model.trim="searchText">
        <button type="submit" class="btn btn-primary">Submit</button>
    </form>
</template>

<style>
header {
    height: 150px;
    background-color: black;
    width: 100%;
}
</style>