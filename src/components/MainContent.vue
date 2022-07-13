<template>
    <div class="card-container">
        <img v-if="movieInfo.poster_path" :src="`http://image.tmdb.org/t/p/w300/${movieInfo.poster_path}`" :alt="movieInfo.name">
        <img v-else src="https://placehold.jp/30/000000/ffffff/300x450.png?text=Copertina+non+disponibile" alt="copertina">
        <div class="info">
            <h2>{{ movieInfo.title }}</h2>
            <div>Titolo Originale: {{ movieInfo.original_title }}</div>
            <div>Lingua: {{ movieInfo.original_language }}</div>
            <div>Voto: {{ parseInt(movieInfo.vote_average/2) }} <i class="fa fa-star" aria-hidden="true"></i></div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MainContent',
    data(){
        return{
            star: ''
        }
    },
    props:{
        movieInfo: Object
    },
    methods:{
        stars(n){
            let star = `<i class="fa fa-star" aria-hidden="true"></i>`;
            for(let i = 1; i <= n/2; i++){
                i += star 
                console.log(star)
            }
            return star
        }
    }
}
</script>

<style lang="scss" scoped>
.card-container{
    text-align: center;
    margin: 20px;
    border: 1px solid white;

    .info{
        display: none;
    }

    &:hover{
        background-color: black;
        color: white;
        width: 300px;
        transform: rotateY(180deg);
        transition-duration: 0.8s;

        .info{
        display: block;
        padding-top: 30px;
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