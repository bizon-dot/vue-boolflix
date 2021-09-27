<template>
  <div id="app">
    <Header @search="searchFilm" />
    <CardsContainer :data = "dataFilm" />
   


  </div>
</template>

<script>
  import Header from './components/Header.vue';
  import CardsContainer from './components/CardsContainer.vue';

  import axios from 'axios';
  
  export default {
    name: 'App',
    components: {
      Header,
      CardsContainer
    },
    data() {
      return {
        //https://api.themoviedb.org/3/search/movie?api_key=b088cb04b38937d2c60babc36cfd68ef&query=matrix
        apiUrl: "https://api.themoviedb.org/3/search/",
        apiKey: 'b088cb04b38937d2c60babc36cfd68ef',
        dataFilm: [],
      }
    },
    methods: {
      getData(apiConf){
        axios
        .get(this.apiUrl + 'movie',apiConf)
        .then(res => {
          console.log(res.data);
          this.dataFilm = res.data.results;

        }).catch(err => {
          console.log("Error ", err);
        })

      },
      searchFilm(inputText) {
        const apiConf = {
          params: {
              api_key: this.apiKey,
              query: inputText
          }
        };
      this.getData(apiConf);
       
      }
    }
  }
</script>

<style lang="scss">
  @import "./style/general.scss";

  #app {

    .intro {
      background: black;
      position: fixed;
      top: 0;
      left: 0;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      width: 100%;
      // height: 100%;
      background-color: white;

      svg {
        width: 10%;
      }
    }



    .container-cards {
      background: $gray-nevada;
    }
  }
</style>