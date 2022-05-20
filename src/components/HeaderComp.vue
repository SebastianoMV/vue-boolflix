<template>
  <header class="d-flex justify-content-between align-items-center">
    Boolflix
    <div>
      <input type="text" v-model="searchMovie">
      <button @click="$emit('functionMovie', searchMovie)">cerca</button>
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderComp',
  data() {
    return {
      searchMovie:''
    }
  },
}
</script>

<style lang="scss" scoped>

header{
  height: 100px;
  background-color: black;
  color: white;
}
</style>