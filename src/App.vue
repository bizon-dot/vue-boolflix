<template>

  <div id="app">
    <Header @search="searchAll" />
    <h1 v-if="(dataFilm.length > 0)"> Films </h1>
    <CardsContainer :data="dataFilm" />
    <CardsContainer :data="dataTv" />
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
      CardsContainer,
    },
    data() {
      return {
        //https://api.themoviedb.org/3/search/movie?api_key=b088cb04b38937d2c60babc36cfd68ef&query=matrix
        apiUrl: "https://api.themoviedb.org/3/search/",
        apiString: '?api_key=',
        apiKey: 'ce4bf3c43722932619dd2d67366a9e66&query=',
        query: '',
        movie: 'movie',
        tv: 'tv',
        dataTv: [],
        dataFilm: [],
      }
    },
    methods: {
        searchAll(input) {
        this.query = input;
        this.searchFilm();
        this.searchTv();
      },

     
      searchFilm() {
        axios
        .get(this.apiUrl + this.movie + this.apiString + this.apiKey + this.query)
        .then(res =>{
          this.dataFilm = res.data.results
        })
      },
      searchTv() {
        axios
        .get(this.apiUrl + this.tv + this.apiString + this.apiKey + this.query)
        .then(res =>{
          this.dataTv = res.data.results
        })
      },
    
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


  //  methods: {
  //     searchAll(){
  //       this.searchFilm;
  //     },
  //     getData(apiConf, type) {
  //       axios
  //         .get(this.apiUrl + type, apiConf)
  //         .then(res => {
  //           this.dataTmp = res.data.results;
  //         }).catch(err => {
  //           console.log("Error ", err);
  //         })
  //     },
  //     searchFilm(inputText) {
  //       const apiConf = {
  //         params: {
  //           api_key: this.apiKey,
  //           query: inputText
  //         }
  //       };
  //       this.getData(apiConf, this.movie);
  //       this.dataFilm = [];
  //       this.dataFilm = this.dataTmp;
  //     },
  //     searchTv(inputText) {
  //       const apiConf = {
  //         params: {
  //           api_key: this.apiKey,
  //           query: inputText
  //         }
  //       };
  //       this.getData(apiConf, this.tv);
  //       this.dataTv = [];
  //       this.dataTv = this.dataTmp;
  //     }
  //   }
</style>