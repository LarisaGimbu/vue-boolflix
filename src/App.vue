<template>
  <div id="app">
    <Header @sendSearch="foundFilm"/>
    <Loader v-if="this.loading"/>
    <Main :films="films"/>
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
      apiURL: 'https://api.themoviedb.org/3/search/movie?',
      apiKey: '9e3e0024fc20b93902720482485f2a3e',
      loading: false
    }
  },
  methods:{
    foundFilm(titolo){
      this.loading = true;

      axios 
        .get(`${this.apiURL}api_key=${this.apiKey}&query=${titolo}&language=it-IT`)
        .then((response) =>{
          this.films = response.data.results;
          console.log(response);
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
