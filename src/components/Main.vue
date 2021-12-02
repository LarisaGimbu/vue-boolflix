<template>
  <main class="container pt-5 ">
    <div 
    v-if="type === 'all' || type === 'films' || type === ''"
    class="film-container">
      <h3>Film:</h3>
      <div class="d-flex justify-content-center flex-wrap">
        <Card  
        v-for="film in films"
        :key="film.id"
        :title="film.title"
        :originalTitle="film.original_title"
        :language="film.original_language"
        :vote="film.vote_average"
        :image="film.poster_path"/>
      </div>
    </div>

    <div 
    v-if="type === 'all' || type === 'series' || type === ''"
    class="serie-container">
      <h3>Serie:</h3>
      <div class="d-flex justify-content-center flex-wrap">
        <Card 
        v-for="serie in series"
        :key="serie.id"
        :title="serie.name"
        :originalTitle="serie.original_name"
        :language="serie.original_language"
        :vote="serie.vote_average"
        :image="serie.poster_path"/>
      </div>
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
    series: Array,
    type: String
  },
  methods:{
 
  }
  
}
</script>

<style lang="scss">

</style>