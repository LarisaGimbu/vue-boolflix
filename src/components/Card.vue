<template>
  <div class="box pe-3">
    <img :src="cardImage" alt="">
    <p><strong>Titolo:</strong> {{title}}</p>
    <p><strong>Titolo originale:</strong> {{originalTitle}}</p>
    <p v-if="language==='it'"><strong>Lingua originale:</strong> <img class="img-language" src="../assets/img/it-flag.jpg" alt=""></p> 
    <p v-else-if="language==='en'"><strong>Lingua originale:</strong> <img class="img-language" src="../assets/img/eng-flag.png" alt=""></p> 
    <p v-else><strong>Lingua originale:</strong> {{language}}</p> 
    <p><strong>Voto:</strong> {{vote}}</p> 
  </div>
</template>

<script>
export default {
  name: 'Card',
  props:{
    title: String,
    originalTitle: String,
    language: String,
    vote: Number,
    image: Image
  },
  data(){
    return{
      cardImage : `https://image.tmdb.org/t/p/w342${this.image}`
    }
  }
}
</script>

<style lang="scss">
.box{
    min-width: 200px;
    .img-language{
      width: 20px;
    }
  }
</style>