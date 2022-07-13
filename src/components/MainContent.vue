<template>
    <div class="card-container">
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