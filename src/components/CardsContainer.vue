<template>
  <main>
    <section class="movies">
      <h2>Films</h2>
      <span class="flag-icon flag-icon-it"></span>
      <ul class="cards">
        <li v-for="(card, index) in data" :key="index">
           
          {{card.title}}
        
          {{card.original_title}}
        
          {{card.vote_average}}
          <span v-bind:class="'flag-icon flag-icon-' + card.original_language"></span>
          
        
         
        </li>

      </ul>
    </section>
  </main>
</template>

<script>
  export default {
    name: 'CardsContainer',
    props: ['data']
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  @import "./style/general.scss";


</style>