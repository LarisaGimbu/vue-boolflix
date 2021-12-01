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


export default {
  name: 'Main',
  data(){
    return{
      
    }
  },
  props:{
    films: Array
  },
  
}
</script>

<style lang="scss">
main{
  .box{
    width: 200px;
  }
}
</style>