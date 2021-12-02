<template>
  <main class="container pt-5 ">
    <h3>Film:</h3>
    <div class="film-container d-flex justify-content-center flex-wrap">
      <Card  
      v-for="film in films"
      :key="film.id"
      :title="film.title"
      :originalTitle="film.original_title"
      :language="film.original_language"
      :vote="film.vote_average"/>
    </div>

    <h3>Serie:</h3>
    <div class="film-container d-flex justify-content-center flex-wrap">
      <Card 
      v-for="serie in series"
      :key="serie.id"
      :title="serie.name"
      :originalTitle="serie.original_name"
      :language="serie.original_language"
      :vote="serie.vote_average"/>
    </div>
  </main>
</template>

<script>
import Card from './Card.vue'

export default {
  name: 'Main',
  components:{
    Card
  },
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

</style>