<template>
<div class="card">
<!-- <img :src="`${urlImg}${image}`" alt="">
  <ul>
    <li>Titolo originale: {{ originalTitle }}</li>
    <li>Lingua: {{ language }}</li>
    <li>Voto: {{ vote }}</li>
  </ul> -->
   <div class="smv-card">
    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img :src="`${urlImg}${image}`" alt="">
        
      </div>
      <div class="flip-card-back">
        <h4>{{ title }}</h4>
        <p>Titolo originale: {{ originalTitle }}</p>
        <p>Lingua: {{ language }}</p>
        <p>Voto: {{ vote }}</p>
      </div>
    </div>
  </div> 
</div> 
</template>

<script>
export default {
  name: 'CardComp',
  data(){
    return{
      urlImg: 'https://image.tmdb.org/t/p/w500',
    }
  },
  props:{
      title : String,
      originalTitle: String,
      language: String,
      vote: Number,
      image: String,
    },
}
</script>

<style lang="scss" scoped>
.card{
  min-width: 250px;
  max-height: 100%;
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
  h4{
    color: white;
  }
  p{
    color: gray;
  }
}
// Flip

.flip-card-inner {
  position: relative;
  min-width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  background-color: black;
}

.smv-card:hover .flip-card-inner {
  transform: rotateY(180deg);
  background-color: black;
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  
  backface-visibility: hidden;
  background-color: black;
 
}

.flip-card-back {
  transform: rotateY(180deg);
  background-color: black;
  h4{
    color: white;
    text-transform: uppercase;
  }
   p{
    color: white;
    font-size: 20px;
    font-weight: 500;
  }
}
</style>