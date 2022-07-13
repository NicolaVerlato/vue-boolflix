<template>
    <div class="card-container">
        <img v-if="seriesInfo.poster_path" :src="`http://image.tmdb.org/t/p/w300/${seriesInfo.poster_path}`" :alt="seriesInfo.name">
        <img v-else src="https://placehold.jp/30/000000/ffffff/300x450.png?text=Copertina+non+disponibile" alt="copertina">
        <div class="info">
            <h2>{{ seriesInfo.name }}</h2>
            <div>Titolo Originale: {{ seriesInfo.original_name }}</div>
            <div>Lingua: {{ seriesInfo.original_language }}</div>

            <div class="valutazione">
                <span>
                    Voto:
                </span>
                <i v-for="number in 5" :key="number" :class="number <= stars(seriesInfo.vote_average) ? 'fa' : 'fa-regular'" class="fa-star" aria-hidden="true"></i>
            </div>

            <div class="overview">
                <div>Overview: {{ seriesInfo.overview }}</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SeriesComponent',
    data(){
        return{
            parseNum: []
        }
    },
    props:{
        seriesInfo: Object
    },
    methods:{
        stars(n){
            this.parseNum = Math.ceil(n/2);
            return this.parseNum
        }
    }
}
</script>

<style lang="scss" scoped>
.card-container{
    margin: 20px;
    border: 1px solid white;

    .info{
        display: none;
    }

    .overview{
        display: none;
    }

    &:hover{
        background-color: black;
        color: white;
        width: 300px;
        transform: rotateY(180deg);
        transition-duration: 0.8s;

        .info{
            padding: 0 10px;
            display: block;
            padding-top: 30px;
            transform: rotateY(180deg);
        }

        .overview{
            display: block;
        }
    } 

    img{
        display: block;
        height: 100%;
    }

    &:hover img{
        display: none;
    }

    i{
        color: #fffe00;
    }
}
</style>