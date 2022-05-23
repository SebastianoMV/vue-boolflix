<template>
<div>
  <h2 class="mt-4">Series</h2>
  <div class="container-fluid d-flex overflow-auto p-0">
    <CardComp v-for="( movie, index ) in listTV" :key="index" :title="movie.title" :originalTitle="movie.original_title" :language="movie.original_language" :vote="movie.vote_average" :image='movie.poster_path' :overview="movie.overview"/>
    
  </div>
</div>
</template>

<script>
import CardComp from './CardComp.vue';
export default {
    name: "CArdComp",
    components: { CardComp },
    props:{
      listTV : Array,
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