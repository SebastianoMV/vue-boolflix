<template>
<div>
  <h2 class="mt-4">Series</h2>
  <div class="container-fluid d-flex overflow-auto p-0">
    <CardComp v-for=" movie in listTV" :key="movie.id" :title="movie.name" :originalTitle="movie.name" :language="movie.original_language" :vote="movie.vote_average" :image='movie.poster_path' :overview="movie.overview" :id="movie.id"/>
    
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


</style>