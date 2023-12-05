<script>
export default {
    name: 'MovieCard',
    props: {
        movie: Object
    },
}
</script>

<template>
    <div class="card">
        <h3>{{ movie.title }}</h3>
        <h6><em>(Original Title: {{ movie.original_title }})</em></h6>
        <h6><em>(Original Language: {{ movie.original_language }})</em></h6>
        <h4>{{ movie.vote_average }}</h4>
    </div>
</template>

<style scoped></style>