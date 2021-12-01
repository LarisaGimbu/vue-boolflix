<template>
  <div id="app">
    <Header @sendSearch="foundFilm"/>
    <Main :films="films"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return{
      films: [],
      apiURL: 'https://api.themoviedb.org/3/search/movie?',
      apiKey: '9e3e0024fc20b93902720482485f2a3e',
    }
  },
  methods:{
    foundFilm(titolo){
       axios 
        .get(`${this.apiURL}api_key=${this.apiKey}&query=${titolo}&language=it-IT`)
        .then((response) =>{
          this.films = response.data.results;

          
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
