<template>
  <main>
    <h2>Movie</h2>
    <MovieComp v-if="!onlyTV==true" :listMovie="listMovie"/>
    <h2 class="mt-4">Series</h2>
    <SeriesComp v-if="!onlyMovie==true" :listMovie="listMovie"/>
    
  </main>
</template>

<script>
import MovieComp from './MovieComp.vue';
import SeriesComp from './SeriesComp.vue';
export default {
    name: "MainComp",
    components: { MovieComp, SeriesComp },
    props:{
      listMovie : Array,
    },
    data(){
      return{
        onlyTV: false,
        onlyMovie: false,
      }
    },
    methods: {
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
main{
  background-color: black;
  height: calc(100% - 100px);
  padding-bottom: 20px;
  h2{
    margin-left: 100px;
    color: lightgrey;
  }
}

</style>