<template>
    <div class="card-container">
        <img v-if="movieInfo.poster_path" :src="`http://image.tmdb.org/t/p/w300/${movieInfo.poster_path}`" :alt="movieInfo.name">
        <img v-else src="https://placehold.jp/30/000000/ffffff/300x450.png?text=Copertina+non+disponibile" alt="copertina">
        <div class="info">
            <h2>{{ movieInfo.title }}</h2>
            <div>Titolo Originale: {{ movieInfo.original_title }}</div>

            <div class="language">
                Lingua: {{ movieInfo.original_language }}
            </div>
            

            <div class="valutazione">
                <span>
                    Voto:
                </span>
                <i v-for="number in 5" :key="number" :class="number <= stars(movieInfo.vote_average) ? 'fa' : 'fa-regular'" class="fa-star" aria-hidden="true"></i>
            </div>
        </div>
        <div class="overview">
            <div>Overview: {{ movieInfo.overview }}</div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MainContent',
    data(){
        return{
            parseNum: []
        }
    },
    props:{
        movieInfo: Object
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
            padding: 0 10px;
            display: block;
            transform: rotateY(180deg);
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