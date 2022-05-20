<template>
  <main>
    <MovieComp :listMovie="listMovie"/>
    <SeriesComp/>
    
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
  height: calc(100vh - 100px);
}

</style>