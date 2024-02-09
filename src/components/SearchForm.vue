<script>

export default {
    name: 'SearchForm',

    data: () => ({
        searchText: ''
    }),
    props: { placeholder: String, buttonLabel: String },
    emits: ['input-text'],
}

</script>

<template>
    <!--FORM-->
    <form @submit.prevent="$emit('input-text', searchText), resetInput" class="d-flex gap-3">
        <input type="text" class="form-control" id="#" v-model.trim="searchText" :placeholder="placeholder">
        <button type="submit" class="btn btn-danger">{{ buttonLabel }}</button>
    </form>
</template>

<style>
header {
    height: 150px;
    background-color: black;
    width: 100%;
}
</style>