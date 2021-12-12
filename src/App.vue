<template>
  <div id="app">
    <Header @sendSearch="foundFilm"
    @sendType="foundType"/>
    <Loader v-if="this.loading"/>
    <Carousel 
    v-if="movie.length == 0 && tv.length == 0"
    :populars="populars"/>


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

export default {
  name: 'App',
  components: {
    Header,
    Loader,
    Main,
    Carousel
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

        console.log(this.popular.results);
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
