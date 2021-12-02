<template>
  <div id="app">
    <Header @sendSearch="foundFilm"/>
    <Loader v-if="this.loading"/>
    <Main 
    v-if="films.length !== 0 || series.length !== 0"
    :films="films"
    :series="series"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import Loader from './components/Loader.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    Loader,
    Main,
  },
  data(){
    return{
      films: [],
      series: [],
      apiUrlMovie: 'https://api.themoviedb.org/3/search/movie',
      apiUrlTv: 'https://api.themoviedb.org/3/search/tv',
      apiParams: {
        api_key: '9e3e0024fc20b93902720482485f2a3e',
        language: 'it-IT',
        query: ''
      },
      
      loading: false
    }
  },
  methods:{
    foundFilm(titolo){
      this.apiParams.query = titolo;
      this.loading = true;

      axios 
        .get(this.apiUrlMovie, {params: this.apiParams})
        .then((response) =>{
          this.films = response.data.results;
          this.loading = false;
          
        })
        .catch((error) =>{
          console.log(error);
        })

      axios
        .get(this.apiUrlTv, {params: this.apiParams})
        .then((response) =>{
          this.series = response.data.results;
          this.loading = false;

        })
        .catch((error) =>{
          console.log(error);
        })
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/general.scss';
@import './assets/style/vars.scss';

</style>
