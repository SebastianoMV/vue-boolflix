<template>
  <div id="app">
    <HeaderComp @functionMovie="functionMovie"/>
    <MainComp/>
    
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
      ciao:'',
      listMovie:[],
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
      query: this.ciao
      }
    })
   .then(response => {
          this.listMovie = response.data.results;
          console.log(this.listMovie);
          
        })
   .catch(function (error) {
    console.log(error);
   })
   },

    functionMovie(selectValue){
      this.ciao = selectValue;
      console.log(this.ciao);
      this.getApi()
    },
  }
}
</script>

<style lang="scss">
@import './assets/style/general';
</style>