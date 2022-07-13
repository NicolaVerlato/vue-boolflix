<template>
    <div class="card-container">
        <img v-if="seriesInfo.poster_path" :src="`http://image.tmdb.org/t/p/w342/${seriesInfo.poster_path}`" :alt="seriesInfo.name">
        <img v-else src="https://placehold.jp/30/000000/ffffff/300x450.png?text=Copertina+non+disponibile" alt="copertina">
        <h2>{{ seriesInfo.name }}</h2>
        <div>Titolo Originale: {{ seriesInfo.original_name }}</div>
        <div>Lingua: {{ seriesInfo.original_language }}</div>
        <div>Voto: {{ seriesInfo.vote_average }}</div>
    </div>
</template>

<script>
export default {
    name: 'SeriesComponent',
    props:{
        seriesInfo: Object
    }
}
</script>

<style lang="scss" scoped>
.card-container{
    padding: 20px;
    text-align: center;
    margin: 10px;
    background-color: lightgreen;
}
</style>