<script>

export default {
    name: 'AppHeader'
}

</script>

<template>
    <header class="d-flex align-items-center justify-content-between">
        <h1 class="text-danger">BOOLFIX</h1>
        <form class="d-flex gap-3">
            <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
            <button type="submit" class="btn btn-primary">Submit</button>
        </form>

    </header>
</template>

<style>
header {
    height: 150px;
    background-color: black;
    width: 100%;
}
</style>