<template>
  <header class="d-flex justify-content-between align-items-center">
    <div>
      <img src="https://boolfix-jdonzelli.netlify.app/img/logo.png" @click="allSelect()" alt="">
      <button class="btn-movie-tv m-3" @click="movieSelect()">Movie</button>
      <button class="btn-movie-tv m-1" @click="tvSelect()">TV</button>
    </div>
    <div>
      <input type="text" v-model="searchMovie" @keyup.enter="serachMovieMethods()">
      <button class="btn btn-danger m-1" @click="serachMovieMethods()">Cerca</button>
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderComp',
  data() {
    return {
      searchMovie:'',
      filterType:'',
    }
  },
  methods: {
    serachMovieMethods(){
      this.$emit( 'functionMovie', this.searchMovie );
      this.searchMovie= '';
    },

    // FUNZIONI SELEZIONE FILTRO EMIT
    movieSelect(){
      this.filterType = 'movie'
      this.$emit( 'movieSelect', this.filterType )
    },
    tvSelect(){
      this.filterType = 'tv'
      this.$emit( 'tvSelect', this.filterType )
    },
    allSelect(){
      this.filterType = 'all'
      this.$emit( 'allSelect', this.filterType )
    },
    

  },
}
</script>

<style lang="scss" scoped>
@import '../assets/style/var';

header{
  height: 100px;
  background-color: black;
  color: white;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 999;
  width: 100%;
  img{
    cursor: pointer;
  }
  .btn{
    background-color: $primary-color;  }
  .btn-movie-tv{
    background-color: black;
    color: white;
    font-size: 22px;
    text-transform: uppercase;
    border: none
    ;
    &:hover{
      opacity: 80%;
    }
  }
}
</style>