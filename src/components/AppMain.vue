<script>

export default {
    name: 'AppMain',
    props: { filmList: Array }
}

</script>

<template>
    <main>
        <ul>
            <li v-for="film in filmList">
                <p>{{ film.title }}</p>
                <p>{{ film.original_title }}</p>
                <p>{{ film.original_language }}</p>
                <p>{{ film.vote_average }}</p>
            </li>
        </ul>
    </main>
</template>

<style></style>