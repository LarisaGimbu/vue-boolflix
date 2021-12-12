<template>
  <div id="app">
    <Header @sendSearch="foundFilm"
    @sendType="foundType"/>
    <Loader v-if="this.loading"/>

    <div class="home"
    v-if="movie.length == 0 && tv.length == 0">
      <Carousel :populars="populars"/>
      <div class="d-flex justify-content-center flex-wrap mt-5">
        <Card 
        v-for="popular in populars"
        :key="popular.id"
        :title="popular.title"
        :originalTitle="popular.original_title"
        :language="popular.original_language"
        :vote="popular.vote_average"
        :image="popular.poster_path"
        :overview="popular.overview"/>
      </div>
      
    </div>


    <Main 
    v-if="movie.length !== 0 || tv.length !== 0"
    :films="movie"
    :series="tv"
    :popular="popular"
    :type="type"/>
    <h3 v-else
    class="text-center">{{notFound}}</h3>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import Loader from './components/Loader.vue'
import axios from 'axios'
import Carousel from './components/Carousel.vue'
import Card from './components/Card.vue'

export default {
  name: 'App',
  components: {
    Header,
    Loader,
    Main,
    Carousel,
    Card
  },
  data(){
    return{
      movie: [],
      tv: [],
      populars: [],
      type:'',
      apiUrlMovie: 'https://api.themoviedb.org/3/search/',
      apiUrlTv: 'https://api.themoviedb.org/3/search/tv',
      apiParams: {
        api_key: '9e3e0024fc20b93902720482485f2a3e',
        language: 'it-IT',
        query: ''
      },
      notFound: '',
      
      loading: false
    }
  },
  methods:{
    foundFilm(titolo){
      this.apiParams.query = titolo;
      this.loading = true;

      this.getApi('movie')
      this.getApi('tv')
    },
    getApi(type){
       axios 
        .get(this.apiUrlMovie+type, {params: this.apiParams})
        .then((response) =>{
          this[type] = response.data.results;
          this.loading = false;
          this.notFound = `Nessun risultato trovato per "${this.apiParams.query}"`
        })
        .catch((error) =>{
          console.log(error);
        })
    },
    foundType(tipo){
      this.type = tipo;
      console.log(this.type);
    }
  },
  mounted(){
    axios
      .get('https://api.themoviedb.org/3/trending/movie/day?', {params: this.apiParams})
      .then((response) =>{
        this.loading = false;
        this.populars = response.data.results;
      })
      .catch((error) =>{
          console.log(error);
        })
  }
}
</script>

<style lang="scss">
@import './assets/style/general.scss';
@import './assets/style/vars.scss';

</style>
