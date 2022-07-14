<template>
    <div class="card-container">
        <img v-if="movieInfo.poster_path" :src="`http://image.tmdb.org/t/p/w300/${movieInfo.poster_path}`" :alt="movieInfo.name">
        <img v-else src="https://placehold.jp/30/000000/ffffff/300x450.png?text=Copertina+non+disponibile" alt="copertina">
        <div class="info">
            <h3>{{ movieInfo.title ? movieInfo.title : movieInfo.name }}</h3>
            <div>Titolo Originale: {{ movieInfo.original_title ? movieInfo.original_title : movieInfo.original_name }}</div>

            <div class="language">
                <span>Lingua: </span> 

                <span v-if="flags.includes(movieInfo.original_language)"><img :src="require(`../assets/img/${movieInfo.original_language}.png`)" :alt="movieInfo.original_language"></span>
                
                <span v-else>{{ movieInfo.original_language }}</span>
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
            parseNum: [],
            flags: ['it', 'en']
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
    margin: 10px;
    border: 1px solid white;

    img{
        display: block;
        height: 100%;
        width: 280px;
    }

    .info{
        display: none;
        padding: 0 10px;
        padding-top: 30px;
    }

    .overview{
        display: none;
        padding: 0 10px;
    }

    &:hover{
        background-color: black;
        color: white;
        min-width: 282px;
        max-width: 282px;
        max-height: 420px;
        overflow-y: auto;
        transform: rotateY(180deg);
        transition-duration: 0.8s;
        cursor: pointer;

        .info{
            display: block;
            transform: rotateY(180deg);
        }

        .overview{
            display: block;
            transform: rotateY(180deg);
        }

        .language{
            display: flex;
        }
        .language img{
            display: block;
            width: 27px;
        }
        img{
            display: none;
        }
    } 

    i{
        color: #fffe00;
    }
}
</style>