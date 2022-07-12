<template>
  <div id="app">
    <header>
      <HeaderComponent @startSearching="startSearch"/>
    </header>

    <main>
      <MainContent v-for="movie, index in movies" :key="index" :movieInfo="movie"/>
    </main>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue'
import MainContent from './components/MainContent.vue'
import axios from "axios"

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainContent
  },
  data(){
      return{
          myApi: 'efb8e071130f0936789711365b3fd8b4',
          movies: [],
          search: ''
      }
  },
  methods:{
      getMovie(){
          axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.myApi}&query=${this.search}`)
          .then((element) => {
            this.movies = element.data.results
            console.log(this.movies)
          })
      },
      startSearch(data){
      this.search = data
      this.getMovie()
    }
  },
}
</script>

<style lang="scss">
main{
    width: 70%;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
}
</style>
