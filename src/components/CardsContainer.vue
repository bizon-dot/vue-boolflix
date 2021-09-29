<template>
  <main>
    <section class="movies">
      <ul class="cards">
        <li v-for="(card, index) in data" :key="index" >
        <Card :card="card"/>
        </li>
      </ul>
    </section>
  </main>
</template>

<script>
  import Card from './Card.vue';

  export default {
    name: 'CardsContainer',
    components: {
        Card
    },
          
    props: ['data']
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  @import "./style/general.scss";

  main{
    
  }

  .movies{
    .cards{
      display:flex;
      flex-wrap: wrap;
      justify-content: center;
     
      
      li{
          list-style: none;
          padding: 30px;
          //flex-basis: 100px;
       
      }
    }
  }


</style>