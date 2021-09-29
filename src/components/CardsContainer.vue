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
      gap: 10px;
      gap: 10px 20px; /* row-gap column gap */
      row-gap: 10px;
      column-gap: 20px;

      li{
          list-style: none;
          flex-basis: 100px;
       // flex: 0 1 calc(20% - 8px);
      }
    }
  }


</style>