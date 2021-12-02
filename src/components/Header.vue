<template>
  <header class="d-flex justify-content-between">
    <div class="logo ps-2">BOOLFLIX</div>
    <div class="input-group mb-3 search-film">
      <input 
      v-model="filmToSearch"
      type="text" 
      class="form-control" 
      placeholder="Inserisci il titolo del film" 
      aria-describedby="button-addon2">
      <button 
      @click="searchFilm()"
      class="btn btn-outline-secondary" 
      type="button" id="button-addon2">Search</button>
    </div>
    <select 
    v-model="type"
    @change="$emit('sendType', type)"
    class="form-select" 
    aria-label="Default select example">
      <option value="all" selected>All</option>
      <option value="films">Films</option>
      <option value="series">Series</option>
    </select>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data(){
    return{
      filmToSearch: '',
      type:''
    }
  },
  methods:{
    searchFilm(){
      console.log('Questo è il parametro che header passa ad APP',this.filmToSearch);
      this.$emit('sendSearch', this.filmToSearch)
    }
  }
}
</script>

<style lang="scss">
@import '../assets/style/vars.scss';

header{
  .logo{
    color: $logo-color;
    font-size: 1.5rem;
  }
  .search-film{
    width: 28%;
    input{
      width: 250px !important;
      flex: none !important;
    }
  } 
  .form-select{
    width: 100px;
    height: 30px;
  }
}
</style>