<template>
  <div id="app">
    <header>
      <HeaderComponent @startSearching="startSearch"/>
    </header>

    <main>
      <section>
        <MainContent v-for="movie in movies" :key="movie.id" :movieInfo="movie"/>
      </section>
      <section>
        <SeriesComponent v-for="series in series" :key="series.id" :seriesInfo="series"/>
      </section>
    </main>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue'
import MainContent from './components/MainContent.vue'
import SeriesComponent from './components/SeriesComponent.vue'
import axios from "axios"

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainContent,
    SeriesComponent
  },
  data(){
      return{
          myApi: 'efb8e071130f0936789711365b3fd8b4',
          movies: [],
          series: [],
          search: '',
          itaFlag: 'https://upload.wikimedia.org/wikipedia/en/thumb/0/03/Flag_of_Italy.svg/255px-Flag_of_Italy.svg.png', 
          usFlag: 'https://upload.wikimedia.org/wikipedia/commons/thumb/e/e2/Flag_of_the_United_States_%28Pantone%29.svg/280px-Flag_of_the_United_States_%28Pantone%29.svg.png'
      }
  },
  computed:{
    filteredMovie(){
      return this.movies.filter((item) => {
        console.log(item)
        if(item.original_language.includes("it")){
          return item.original_language = this.itaFlag; 
        }
         
      })
    },
  //   filteredSeries(){
  //     return this.series.filter((item) => {
  //       return  item.name.toLowerCase().includes(this.search.toLowerCase());  
  //     })
  //   }
  },
  methods:{
      getMovie(){
        // chiamata per film
        axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.myApi}&query=${this.search}`)
        .then((element) => {
          this.movies = element.data.results;
        })
      },
      getSeries(){
        // chiamata per serie tv
        axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.myApi}&language=it_IT&query=${this.search}`)
        .then((element) => {
          this.series = element.data.results;
        })
      },
      startSearch(text){
      this.search = text;
      this.getMovie();
      this.getSeries();
    }
  },
}
</script>

<style lang="scss">
@import './style/common';

section{
    width: 80%;
    margin: 0 auto;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
}
</style>
