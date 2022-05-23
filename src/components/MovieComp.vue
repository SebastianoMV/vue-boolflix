<template>
<div>
  <h2>Movie</h2>
  <div class="container-fluid d-flex overflow-auto p-0">
    <CardComp v-for="movie in listMovie" :key="movie.id" :title="movie.title" :originalTitle="movie.original_title" :language="movie.original_language" :vote="movie.vote_average" :image='movie.poster_path' :overview="movie.overview"/>
    
  </div>
  </div>
</template>

<script>
import CardComp from './CardComp.vue';
export default {
    name: "MovieComp",
    components: { CardComp },
    props:{
      listMovie : Array,
    },

    
}
</script>

<style lang="scss" scoped>
@import '../assets/style/var';
@import '../assets/style/utilities';
h2{
    margin-left: 100px;
    color: lightgrey;
  }

</style>