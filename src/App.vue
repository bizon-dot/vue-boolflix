<template>
  <div id="app">
    <Header @search="searchFilm" />
    
  </div>
</template>

<script>
import Header from './components/Header.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header
  }, 
  data(){
    return {
      endPoint: "https://api.themoviedb.org/3/search/movie?api_key=b088cb04b38937d2c60babc36cfd68ef&language=en-US&query=",
    }
  },
  methods: {
    searchFilm(inputText){
      console.log(inputText);
      let uri = this.endPoint + inputText;
      console.log(uri);
       axios.get(uri).then(res => {
          console.log(res.data);
         
         
        }).catch(err => {
          console.log("Error ", err);
        })
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
