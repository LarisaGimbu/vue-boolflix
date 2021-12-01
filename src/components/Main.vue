<template>
  <main class="container pt-5 ">
    <h3>Film:</h3>
    <div class="film-container d-flex justify-content-center flex-wrap">
      <div
      class="box pe-3" 
      v-for="(film, index) in films"
      :key="index">
        <p><strong>Titolo:</strong> {{film.title}}</p>
        <p><strong>Titolo originale:</strong> {{film.original_title}}</p>
        <p v-if="film.original_language==='it'"><strong>Lingua originale:</strong> <img src="../assets/img/it-flag.jpg" alt=""></p> 
        <p v-else-if="film.original_language==='en'"><strong>Lingua originale:</strong> <img src="../assets/img/eng-flag.png" alt=""></p> 
        <p v-else><strong>Lingua originale:</strong> {{film.original_language}}</p> 
        <p><strong>Voto:</strong> {{film.vote_average}}</p> 
      </div>
    </div>

    <h3>Serie:</h3>
    <div class="film-container d-flex justify-content-center flex-wrap">
      <div
      class="box pe-3" 
      v-for="serie in series"
      :key="serie.id">
        <p><strong>Titolo:</strong> {{serie.name}}</p>
        <p><strong>Titolo originale:</strong> {{serie.original_name}}</p>
        <p v-if="serie.original_language==='it'"><strong>Lingua originale:</strong> <img src="../assets/img/it-flag.jpg" alt=""></p> 
        <p v-else-if="serie.original_language==='en'"><strong>Lingua originale:</strong> <img src="../assets/img/eng-flag.png" alt=""></p> 
        <p v-else><strong>Lingua originale:</strong> {{serie.original_language}}</p> 
        <p><strong>Voto:</strong> {{serie.vote_average}}</p> 
      </div>
    </div>
  </main>
</template>

<script>

export default {
  name: 'Main',
  data(){
    return{
     
    }
  },
  props:{
    films: Array,
    series: Array
  },
  methods:{
 
  }
  
}
</script>

<style lang="scss">
main{
  .box{
    width: 200px;
    img{
      width: 20px;
    }
  }
}
</style>