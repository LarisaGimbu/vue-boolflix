<template>
  <header class="d-flex justify-content-between">
    <div class="logo ps-2">BOOLFLIX</div>
    <div class="input-group mb-3 search-film">
      <input type="text" class="form-control" placeholder="Inserisci il titolo del film" aria-describedby="button-addon2">
      <button class="btn btn-outline-secondary" type="button" id="button-addon2">Search</button>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header'
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
}
</style>