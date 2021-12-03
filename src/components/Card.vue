<template>
  <div class="box pe-3 pb-3">

    <div class="flip-card ">
      <div class="flip-card-inner ">
        <div class="flip-card-front">
          <img :src="cardImage" alt="">
        </div>
        <div class="flip-card-back d-flex flex-column justify-content-center align-items-center">
          <p><strong>Titolo:</strong> {{title}}</p>
          <p><strong>Titolo originale:</strong> {{originalTitle}}</p>
          <div><strong>Lingua originale:</strong> 
            <img v-if="flags.includes(language)" class="img-language" :src="require(`../assets/img/${language}.png`)" alt="">
            <span v-else>{{language}}</span>
          </div> 
          <p><strong>Voto:</strong>
            <span >
              <i 
              v-for="(star, index) in 5" :key="index"
              class="fa-star"
              :class="index<=starsNumber? 'fas': 'far'"></i>
            </span>
          </p> 
        </div>
      </div>
    </div>


    
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
      cardImage : '',
      flags:['it', 'en'],
      starsNumber: Math.round(this.vote/2)
    }
  },
  methods:{
    cardPoster(){
      if(this.image != undefined){
        this.cardImage = `https://image.tmdb.org/t/p/w342${this.image}`;
        
      }else{
        this.cardImage = 'https://m.media-amazon.com/images/I/41n1xmnsn8L._AC_.jpg';
      }
    }
  },
  mounted(){
    this.cardPoster()
  }
}
</script>

<style lang="scss">
.box{
    min-width: 200px;
    .img-language{
      width: 20px;
    }
    
    .flip-card {
      width: 350px;
      height: 515px;
      perspective: 1000px; 
    }
    .flip-card-inner {
      position: relative;
      width: 100%;
      height: 100%;
      text-align: center;
      transition: transform 0.8s;
      transform-style: preserve-3d;
    }
    .flip-card:hover .flip-card-inner {
      transform: rotateY(180deg);
    }
    .flip-card-front, .flip-card-back {
      position: absolute;
      width: 100%;
      height: 100%;
      -webkit-backface-visibility: hidden; /* Safari */
      backface-visibility: hidden;
    }
    .flip-card-back {
      background-color: black;
      color: white;
      transform: rotateY(180deg);
    }
  }
</style>