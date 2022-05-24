<template>
<div class="card overflow-hidden">
   <div class="smv-card">
    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img v-if="image == null" class="img-null" src="https://www.frosinonecalcio.com/wp-content/uploads/2021/09/default-placeholder.png" alt="">
        <img v-else :src="`${urlImg}${image}`" alt="">
        
      </div>
      <div class="flip-card-back" @click="movieDetails()">
        <h4>{{ title }}</h4>
        <p>Titolo originale: {{ originalTitle }}</p>
        <div v-if="language == 'en'"><img src="../assets/img/en.svg" alt=""></div>
        <div v-else-if="language == 'it'"><img src="../assets/img/it.svg" alt=""></div>
        <p v-else>Lingua: {{language}}</p>
        <div>
          <span v-for="n in 5" :key="n">
           <span v-if="voto >= n">
            <i class="fa-solid fa-star"></i>
           </span>
           <span v-else>
            <i class="fa-regular fa-star"></i>
           </span>
          </span>
        </div>
        <div v-if="details == true">
          <div> 
            <span class="red-text">Generi:</span>
            <span v-for="(genre, index) in movieGenre" :key="index">{{genre.name}} </span> 
          </div>
          <div> 
            <span class="red-text">Attori:</span>
            <span v-for="(cast, index) in movieCast" :key="index">{{cast.name}} </span> 
          </div>
        </div>
        <p v-else class="overview">{{overview}}</p>
        
      </div>
    </div>
  </div> 
</div> 
</template>

<script>
import axios from 'axios';

export default {
  name: 'CardComp',
  data(){
    return{
      urlImg: 'https://image.tmdb.org/t/p/w342',
      voto: Math.round( this.vote / 2 ),
      apiMovieGenre: `https://api.themoviedb.org/3/${this.keyMovieTV}/${this.id}?`,
      apiMovieCast: `https://api.themoviedb.org/3/${this.keyMovieTV}/${this.id}/credits?`,
      apiObject:{
        api_key: '71534d03a5cf96ab640c43e968229013',
        language: 'it-IT',
      },
      movieGenre:[],
      movieCast:[],
      details: false,
      
    }
  },
  props:{
      title : String,
      originalTitle: String,
      language: String,
      vote: Number,
      image: String,
      overview: String,
      id: Number,
      keyMovieTV: String,
      
    },

  methods:{
    getApiId(){
    axios.get(this.apiMovieGenre, {
    params: this.apiObject
    })
    .then(response => {
        this.movieGenre = response.data.genres;
        console.log(this.movieGenre);
    })
    .catch(error => {
        console.log(error);    
    })
    },

    getApiCast(){
    axios.get(this.apiMovieCast, {
    params: this.apiObject
    })
    .then(response => {
      console.log(response);
        this.movieCast = response.data.cast;
        this.movieCast.length = 5;
        console.log(this.movieCast);
    })
    .catch(error => {
        console.log(error);    
    })
    },
    
    movieDetails(){
      this.details = !this.details;
      console.log(this.id);
      this.getApiId();
      this.getApiCast()
    }


  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/var';

.card{
  min-width: 250px;
  max-height: 350px;
  margin: 5px;
  border: none;
  background-color: black;
  
}
.smv-card{
  width: 100%;
  height: 100%;

  img{
    width: 100%;
    height: 100%;
  }
}
// Flip

.flip-card-inner {
  position: relative;
  min-width: 100%;
  height: 350px;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  background-color: black;
}

.smv-card:hover .flip-card-inner {
  transform: rotateY(180deg);
  background-color: black;
   .overview{
    height: 100px;
    overflow-y: auto;
  }
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 350px;
  backface-visibility: hidden;
  background-color: black;
 
}

.flip-card-back {
  transform: rotateY(180deg);
  background-color: black;
  h4{
    color: $primary-color;
    text-transform: uppercase;
  }
   p, span{
    color: white;
    font-size: 12px;
    font-weight: 500;
  }
  span{
    font-size: 15px;
    &.red-text{
      color: $primary-color;
    }
  }
  img{
    width: 20px;
  }
  i{
    color: gold;
    font-size: 20px;
  }
}
</style>