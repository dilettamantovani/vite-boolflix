<script>
export default {
    name: 'SeriesCard',
    props: {
        series: Object
    },
}
</script>

<template>
    <div class="card" id="seriesCard">
        <h3>{{ series.name }}</h3>
        <h6><em>(Original Title: {{ series.original_name }})</em></h6>
        <h6><em>(Original Language: {{ series.original_language }})</em></h6>
        <h4>{{ series.popularity }}</h4>
    </div>
</template>

<style scoped>
#seriesCard {
    background-color: blueviolet;
}
</style>