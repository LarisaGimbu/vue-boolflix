<template>
  <div class="box pe-3">
    <img :src="cardImage" alt="">
    <p><strong>Titolo:</strong> {{title}}</p>
    <p><strong>Titolo originale:</strong> {{originalTitle}}</p>
    <p v-if="language==='it'"><strong>Lingua originale:</strong> <img class="img-language" src="../assets/img/it-flag.jpg" alt=""></p> 
    <p v-else-if="language==='en'"><strong>Lingua originale:</strong> <img class="img-language" src="../assets/img/eng-flag.png" alt=""></p> 
    <p v-else><strong>Lingua originale:</strong> {{language}}</p> 
    <p><strong>Voto:</strong>
      <span v-for="(star, index) in stars" :key="index">
        <i class="fas fa-star"></i>
      </span>
      <span v-for="(emptyStar, index) in emptyStars" :key="index">
        <i class="far fa-star"></i>
      </span>
    </p> 
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
    image: String
  },
  data(){
    return{
      cardImage : `https://image.tmdb.org/t/p/w342${this.image}`,
      starsNumber: 0,
      stars: [],
      emptyStars:[]
    }
  },
  methods:{
    voteStars(vote){
      this.starsNumber = Math.ceil(vote/2);
      console.log('Questo è il voto in decimali',vote);
      console.log('Questo è il voto diviso due',this.starsNumber);

      for(let i=1; i<= (this.starsNumber); i++){
        this.stars.push(i)
      }
      for(let i=1; i<= (5-this.starsNumber); i++){
        this.emptyStars.push(i)
      }

      console.log('queste sono le stelle piene', this.stars);
      console.log('queste sono le stelle vuote', this.emptyStars);
    }
  },
  mounted(){
    this.voteStars(this.vote)
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