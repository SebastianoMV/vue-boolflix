<template>
  <main>

    <!-- MOVIE COMP APPARE SE NON é SELEZIONATO IL FILTRO 'tv' E SE L'ARRAY LISTMOVIE é PIENO -->
    <MovieComp v-if="filterType != 'tv' && listMovie.length > 0" :listMovie="listMovie"/>
    
    <!-- SERIES COMP APPARE SE NON é SELEZIONATO IL FILTRO 'movie' E SE L'ARRAY LISTTV é PIENO -->
    <SeriesComp v-if="filterType != 'movie' && listTV.length > 0" :listTV="listTV"/>
    
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
      listTV : Array,
      filterType : String,
    },
    data(){
      return{
        
      }
    },
    methods: {
      
    },
}
</script>

<style lang="scss" scoped>
main{
  background-color: black;
  height: calc(100% - 100px);
  padding-bottom: 20px;
  padding-top: 100px;
}

</style>