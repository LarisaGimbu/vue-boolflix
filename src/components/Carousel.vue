<template>
  <div class="carousel">
    <h3>I più popolari:</h3>
    <div id="carouselExampleCaptions" class="carousel slide" data-bs-ride="carousel">
      <div class="carousel-indicators">
        <button 
        v-for="(popular, index) in populars"
        :key="index"
        :class="{'active': index==contatore}"
        type="button" data-bs-target="#carouselExampleCaptions" :data-bs-slide-to="index" aria-current="true" :aria-label="`Slide ${index}`"></button>
      </div>
      <div class="carousel-inner">
        <div 
        v-for="(popular, index) in populars"
        :key="popular.id"
        :class="{'active': index==contatore}"
        class="carousel-item">
        <!-- 350x140 -->
          <img :src="`https://image.tmdb.org/t/p/w500/${popular.backdrop_path}`" class="d-block w-100" alt="...">
          <div class="carousel-caption d-none d-md-block">
            <h3>{{popular.title}}</h3>
            <p>{{popular.overview}}</p>
          </div>
        </div>
      </div>
      <button 
      @click="goPrev()"
      class="carousel-control-prev" type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button 
      @click="goNext()"
      class="carousel-control-next" type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Carousel',
  props:{
    populars: Array
  },
  data(){
    return{
      contatore: 0
    }
  },
  methods:{
    goPrev(){
      this.contatore--;
      if(this.contatore < 0) this.contatore = this.populars.length -1;
    },
    goNext(){
      this.contatore++;
      if(this.contatore > this.populars.length -1) this.contatore = 0;
    }
  }
}
</script>

<style lang='scss'>
.carousel{
  max-width: 80%;
  margin: 0 auto;
  .carousel-inner{
    box-shadow: 5px 5px 20px black;
    img{
      width: 100%;
    }
    h3,p{
      text-shadow: 1px 2px 1px black;
    }
    h3{
      font-weight: bold;
    }
    p{
      max-height: 100px;
      overflow-y: auto;
    }
  }
  
}

</style>