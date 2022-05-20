<template>
<div class="card">Titolo: {{ title }}
  <ul>
    <li>Titolo originale: {{ originalTitle }}</li>
    <li>Lingua: {{ language }}</li>
    <li>Voto: {{ vote }}</li>
  </ul>
</div>
</template>

<script>
export default {
  name: 'CardComp',
  props:{
      title : String,
      originalTitle: String,
      language: String,
      vote: Number,
    },
}
</script>

<style lang="scss" scoped>
.card{
  min-width: 300px;
  height: 400px;
}

</style>