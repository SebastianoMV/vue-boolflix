<template>
  <div id="app">
    <HeaderComp @functionMovie="functionMovie"/>

    <div v-if="errorLoading">
    Inserisci un parametro
    </div>

    <div v-else>
    <MainComp :listMovie="listMovie"/>
    </div>
    
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';
import axios from 'axios';


export default {
  name: 'App',

  components: {
    HeaderComp,
    MainComp
  },

  data(){
    return{
      apiUrl: 'https://api.themoviedb.org/3/search/movie',
      api_key: '71534d03a5cf96ab640c43e968229013',
      language: 'it-IT',
      query:'',
      searchMovie:'',
      listMovie:[],
      errorLoading:false,
    }
  },


  mounted(){
    this.getApi();
  },


  methods: {
    getApi(){
    axios.get(this.apiUrl, {
      params: {
      api_key: '71534d03a5cf96ab640c43e968229013',
      language: 'it-IT',
      query: this.searchMovie
      }
    })
   .then(response => {
          this.listMovie = response.data.results;
          console.log(this.listMovie);
          this.errorLoading = false;
          
        })
   .catch(error => {
          console.log(error);
          this.errorLoading = true;
          
        })
   },

    functionMovie(selectValue){
      this.searchMovie = selectValue;
      console.log(this.searchMovie);
      this.getApi()
    },
  }
}
</script>

<style lang="scss">
@import './assets/style/general';
</style>