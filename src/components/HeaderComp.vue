<template>
  <header class="d-flex justify-content-between align-items-center">
    <a href="#"><img src="https://boolfix-jdonzelli.netlify.app/img/logo.png" alt=""></a>
    <div>
      <input type="text" v-model="searchMovie" @keyup.enter="serachMovie()">
      <button class="btn btn-danger m-1" @click="serachMovie()">Cerca</button>
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderComp',
  data() {
    return {
      searchMovie:'',
    }
  },
  methods: {
    serachMovie(){
      this.$emit( 'functionMovie', this.searchMovie );
      this.searchMovie= '';
    }
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
}
</style>