<template>
  <div class="box pe-3">
    <p><strong>Titolo:</strong> {{title}}</p>
    <p><strong>Titolo originale:</strong> {{originalTitle}}</p>
    <p v-if="language==='it'"><strong>Lingua originale:</strong> <img src="../assets/img/it-flag.jpg" alt=""></p> 
    <p v-else-if="language==='en'"><strong>Lingua originale:</strong> <img src="../assets/img/eng-flag.png" alt=""></p> 
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
    vote: Number
  }
}
</script>

<style lang="scss">
.box{
    width: 200px;
    img{
      width: 20px;
    }
  }
</style>