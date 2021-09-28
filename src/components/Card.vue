<template>
  <li>
    <img v-if="card.poster_path"
    :src="'https://image.tmdb.org/t/p/w342' + card.poster_path"
    :alt="card.title ? card.title : card.name">
    <img v-else
    src="https://media.istockphoto.com/photos/cool-placeholder-for-your-picture-no-movie-screen-35mm-film-strip-picture-id1068817392?k=6&m=1068817392&s=170667a&w=0&h=hNRjLOOQ0p0iBsSsGZzi0lDWd9eCY0IK4jNQI5sVYVI="
    />
    <div >
      <i v-for= "n in 5" :key="n" class="fa-star" :class="(n <= getVote()) ? 'fas' : 'far'"></i>
    </div>
    <br />

    {{card.title ? card.title : card.name}}

    {{card.original_title}}

    {{card.vote_average}}

    {{card.original_language}}

    <span v-if="card.original_language == 'en'" class="flag-icon flag-icon-gb-eng"></span>
    <span v-else v-bind:class="'flag-icon flag-icon-' + card.original_language"></span>

    <!-- <img :src="'https://image.tmdb.org/t/p/w342' + card.poster_path"> -->

  </li>

</template>

<script>
  export default {
    name: 'Card',
    props: ["card"],
    methods: {
      getVote(){
        return Math.ceil(this.card.vote_average / 2)
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">


</style>