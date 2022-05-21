<template>
  <div class="container-fluid d-flex overflow-auto p-0">
    <CardComp v-for="( movie, index ) in listMovie" :key="index" :title="movie.title" :originalTitle="movie.original_title" :language="movie.original_language" :vote="movie.vote_average" :image='movie.poster_path'/>
    
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

.container-fluid{
  width: 90%;
  height: 400px;
}
::-webkit-scrollbar{
  height: 10px;
}
::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 20px;
}
::-webkit-scrollbar-thumb {
  background: $primary-color;
  border-radius: 20px;
}

</style>