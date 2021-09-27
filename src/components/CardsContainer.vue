<template>
  <main>
    <section class="movies">
      <h2>Films</h2>
      <ul class="cards">
        <li v-for="(card, index) in data" :key="index">
           
          {{card.title}}
        
          {{card.original_title}}
        
          {{card.vote_average}}
        
          {{card.original_language}}
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


</style>