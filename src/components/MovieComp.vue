<template>
  <div class="container-fluid d-flex overflow-auto">
    <CardComp v-for="( movie, index ) in listMovie" :key="index" :title="movie.title" :originalTitle="movie.original_title" :language="movie.original_language" :vote="movie.vote_average"/>
    
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
::-webkit-scrollbar{
  height: 10px;
}
::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 20px;
}
::-webkit-scrollbar-thumb {
  background: red;
  border-radius: 20px;
}

</style>