<script>

export default {
    name: 'SearchForm',
    data: () => ({
        searchText: ''
    }),
    props: { placeholder: String, buttonLabel: String },
    emits: ['input-text'],
    methods: {

        //FUNZIONE CHE CHIAMA UN EVENTO E RESETTA L'INPUT
        submitForm() {
            this.$emit('input-text', this.searchText);
            this.resetInput();
        },
        //FUNZIONE CHE RESETTA TESTO DELL'IINPUT
        resetInput() {
            this.searchText = '';
        },
    }
}
</script>

<template>
    <!--FORM-->
    <form @submit.prevent="handleSubmit" class="d-flex gap-3">
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