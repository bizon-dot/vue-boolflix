<template>

  <div id="app">
    <Header @search="searchAll" />
    <div class="container">
      <div v-if="(loading)">
        <h1> Films </h1>
        <CardsContainer :data="dataFilm" />
        <CardsContainer :data="dataTv" />
      </div>
      <div v-else>
        <h1> Most Popular </h1>
        <CardsContainer :data="dataTrending" />
       
      </div>
    </div>
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
        apiUrl: "https://api.themoviedb.org/3/search/",
        apiUrlTrending: " https://api.themoviedb.org/3/trending/all/day",
        apiString: '?api_key=',
        apiKey: 'ce4bf3c43722932619dd2d67366a9e66&query=',
        query: '',
        movie: 'movie',
        tv: 'tv',
        dataTv: [],
        dataFilm: [],
        dataTrending: [],
        loading: false,
      }
    },
    created: function () {
      axios
        .get(this.apiUrlTrending + this.apiString + this.apiKey)
        .then(res => {
          this.dataTrending = res.data.results;
        })

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
          .then(res => {
            this.dataFilm = res.data.results;
            this.loading = true;
          })
      },
      searchTv() {
        axios
          .get(this.apiUrl + this.tv + this.apiString + this.apiKey + this.query)
          .then(res => {
            this.dataTv = res.data.results
          })
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

    .container {
      background: $gray-nevada;


      margin: 0 auto;
    }
  }
</style>