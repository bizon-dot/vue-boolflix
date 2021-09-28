<template>
 <li>
           
          {{card.title}}
        
          {{card.original_title}}
        
          {{card.vote_average}}
     
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
