<template>
  <div id="app">
    <Header @search="searchFilm" />
    
  </div>
</template>

<script>
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header
  }, 
  methods: {
    searchFilm(inputText){
      console.log(inputText);
    }
  }
}
</script>

<style lang="scss">
@import "./style/general.scss";
#app {

 /*  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
}
</style>
