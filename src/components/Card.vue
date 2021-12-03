<template>
  <div class="box pe-3 pb-3">
    <img :src="cardImage" alt="">
    <div class="content">
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
    .content{
      display: none;
    }
  }
</style>