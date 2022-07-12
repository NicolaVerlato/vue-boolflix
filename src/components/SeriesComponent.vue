<template>
    <div class="card-container">
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
    width: calc(20% - 20px);
    text-align: center;
    margin: 10px;
}
</style>