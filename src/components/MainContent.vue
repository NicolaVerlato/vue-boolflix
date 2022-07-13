<template>
    <div class="card-container">
        <img v-if="movieInfo.poster_path" :src="`http://image.tmdb.org/t/p/w300/${movieInfo.poster_path}`" :alt="movieInfo.name">
        <img v-else src="https://placehold.jp/30/000000/ffffff/300x450.png?text=Copertina+non+disponibile" alt="copertina">
        <h2>{{ movieInfo.title }}</h2>
        <div>Titolo Originale: {{ movieInfo.original_title }}</div>
        <div>Lingua: {{ movieInfo.original_language }}</div>
        <div>Voto: {{ movieInfo.vote_average }}</div>
    </div>
</template>

<script>
export default {
    name: 'MainContent',
    props:{
        movieInfo: Object
    }
}
</script>

<style lang="scss" scoped>
.card-container{
    padding: 20px;
    text-align: center;
    margin: 10px;
    background-color: lightcoral;

}
</style>