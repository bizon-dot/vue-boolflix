<template>

  <div class="flip-card">
    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img v-if="card.poster_path" :src="'https://image.tmdb.org/t/p/w342' + card.poster_path"
          :alt="card.title ? card.title : card.name" style="width:342px;height:500px;">
        <img v-else
          src="https://images.hindustantimes.com/tech/img/2020/10/28/960x540/2020-10-14T025403Z_1_LYNXMPEG9D04M_RTROPTP_3_INDIA-NETFLIX_1603252067036_1603252079667_1603863087635.JPG"
          style="width:342px;height:500px;" />

      </div>
      <div class="flip-card-back">
        <h4>Titolo: {{card.title ? card.title : card.name}}</h4>
        <h4>Titolo originale: {{card.original_title}}</h4>
        <div>
          <h4>Rating</h4><i v-for="n in 5" :key="n" class="fa-star" :class="(n <= getVote()) ? 'fas' : 'far'" style="color:yellow"></i>
        </div>
        <h4>Overview: {{card.overview}}</h4>

      </div>
    </div>
  </div>



</template>

<script>
  export default {
    name: 'Card',
    props: ["card"],
    methods: {
      getVote() {
        return Math.ceil(this.card.vote_average / 2)
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .flip-card {
    background-color: transparent;
    width: 342px;
    height: 500px;

  }

  /* This container is needed to position the front and back side */
  .flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.8s;
    transform-style: preserve-3d;
  }

  /* Do an horizontal flip when you move the mouse over the flip box container */
  .flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
  }

  /* Position the front and back side */
  .flip-card-front,
  .flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    /* Safari */
    backface-visibility: hidden;

    h4 {
      color: white;
    }
  }

  /* Style the front side (fallback if image is missing) */
  .flip-card-front {

    color: black;
  }

  /* Style the back side */
  .flip-card-back {
    background-color: black;

    transform: rotateY(180deg);
  }
</style>