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
        movie: 'movie',
        tv: 'tv',
        dataTmp:[],
        dataTv: [],
        dataFilm: [],
      }
    },
    methods: {
      getData(apiConf, type){
        axios
        .get(this.apiUrl + type,apiConf)
        .then(res => {
         
          this.dataTmp = res.data.results;
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
        
       this.getData(apiConf, this.movie);
       this.dataFilm = this.dataTmp;
      },
      searchTv(inputText) {
        const apiConf = {
          params: {
              api_key: this.apiKey,
              query: inputText
          }
        };
        
      this.getData(apiConf, this.tv);
      this.dataTv = this.dataTmp;
       
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