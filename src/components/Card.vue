<template>
  <li >

    <!-- {{card}} -->

   

   {{card.title}}

    {{card.original_title}}

    {{card.vote_average}}
    
    {{card.original_language}}
    <span v-if="card.original_language == 'en'" class="flag-icon flag-icon-gb-eng"></span>
    <span v-bind:class="'flag-icon flag-icon-' + card.original_language"></span> 

  </li>

</template>

<script>
  export default {
    name: 'Card',
    props: ["card"]
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">


</style>