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
    }
  },

  methods:{
    getApi(){
      axios
        .get('https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=ritorno+al+futuro')
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