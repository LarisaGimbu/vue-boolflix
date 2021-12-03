<template>
  <div class="box pe-3 pb-3">

    <div class="flip-card ">
      <div class="flip-card-inner ">
        <div class="flip-card-front">
          <img :src="cardImage" alt="">
        </div>
        <div class="flip-card-back d-flex flex-column justify-content-center align-items-center">
          <h3>{{title}}</h3>
          <p><strong>Titolo originale:</strong> {{originalTitle}}</p>
          <div><strong>Lingua originale:</strong> 
            <img v-if="flags.includes(language)" class="img-language ps-2" :src="require(`../assets/img/${language}.png`)" alt="">
            <span v-else>{{language}}</span>
          </div> 
          <p><strong>Voto:</strong>
            <span class="ps-2">
              <i 
              v-for="(star, index) in 5" :key="index"
              class="fa-star"
              :class="index<=starsNumber? 'fas': 'far'"></i>
            </span>
          </p> 
          <div class="description container">
            <strong>Descrizione:</strong>
            <p v-if="overview != ''">{{overview}}</p>
            <p v-else>Non disponibile</p>
          </div>
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
    image: String,
    overview: String
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
        this.cardImage = `https://via.placeholder.com/346x515/000000/FFFFFF/?text=${this.title}`;
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
      width: 25px;
    }
    .description{
      overflow-y: scroll;
      height: 250px;
      font-size: 0.8rem;
    }
    
    .flip-card {
      width: 342px;
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