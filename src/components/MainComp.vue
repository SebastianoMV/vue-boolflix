<template>
  <main>
    <h2>Movie</h2>
    <MovieComp :listMovie="listMovie"/>
    <h2 class="mt-4">Series</h2>
    <SeriesComp :listMovie="listMovie"/>
    
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