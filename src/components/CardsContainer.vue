<template>
  <main>
    <section class="movies">
      <h2>Films</h2>
     
      <ul class="cards">
        <Card v-for="(card, index) in data" :key="index"/>
   
      </ul>
    </section>
  </main>
</template>

<script>
  import Card from './Card.vue';

  export default {
    name: 'CardsContainer',
    componets: {
        Card
    },
          
    props: ['data']
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  @import "./style/general.scss";


</style>