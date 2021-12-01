<template>
  <main class="container pt-5 d-flex justify-content-center flex-wrap">
    <div
    class="box pe-3" 
    v-for="(film, index) in films"
    :key="index">
      <p><strong>Titolo:</strong> {{film.title}}</p>
      <p><strong>Titolo originale:</strong> {{film.original_title}}</p>
      <p><strong>Lingua originale:</strong> {{film.original_language}}</p> 
      <p><strong>Voto:</strong> {{film.vote_average}}</p> 
    </div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Main',
  data(){
    return{
      films: [],
      apiURL: 'https://api.themoviedb.org/3/search/movie?',
      apiKey: '9e3e0024fc20b93902720482485f2a3e',
      titleFilm: 'ritorno+al+futuro'
    }
  },

  methods:{
    getApi(){
      axios 
        .get(`${this.apiURL}api_key=${this.apiKey}&query=${this.titleFilm}`)
        .then((response) =>{
          this.films = response.data.results;

          
        })
        .catch((error) =>{
          console.log(error);
        })
    }
  },
  mounted(){
    this.getApi()
  }
}
</script>

<style lang="scss">
main{
  .box{
    width: 200px;
  }
}
</style>