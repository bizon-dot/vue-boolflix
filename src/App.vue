<template>
  <div id="app">
    <Header @search="searchFilm" />
   <!--  <div class="intro" v-if="(dataFilm.length < 1)">
    <font-awesome-icon icon="user-secret" />
    </div> -->

    <div class="container-cards">
      <div v-for="(film, index) in dataFilm" :key="index">
        <!-- {{film}} -->
        <p>
          {{film.title}}
        </p>
        <p>
          {{film.original_title}}
        </p>
        <p>
          {{film.vote_average}}
        </p>
        <p>
          {{film.original_language}}
        </p>
      </div>

    </div>
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