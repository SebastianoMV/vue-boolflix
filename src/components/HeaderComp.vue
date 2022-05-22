<template>
  <header class="d-flex justify-content-between align-items-center">
    <div>
      <img src="https://boolfix-jdonzelli.netlify.app/img/logo.png" alt="">
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
      onlyTV: false,
      onlyMovie: false,
    }
  },
  methods: {
    serachMovieMethods(){
      this.$emit( 'functionMovie', this.searchMovie );
      this.searchMovie= '';
    },
    movieSelect(){
      this.onlyMovie = true;
      console.log('movie' + this.onlyMovie);
      if(this.onlyTV == true){
        this.onlyTV = false;
        console.log('tv' + this.onlyTV);
      }
    },
    tvSelect(){
      this.onlyTV = true;
      console.log('tv' + this.onlyTV);
      if(this.onlyMovie == true){
        this.onlyMovie = false;
        console.log('movie' + this.onlyMovie);
      }
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