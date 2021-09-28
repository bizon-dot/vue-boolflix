<template>
  <li>
    <div class="flip-card">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <img v-if="card.poster_path" :src="'https://image.tmdb.org/t/p/w342' + card.poster_path"
            :alt="card.title ? card.title : card.name" style="width:342px;height:auto;margin-bottom:50px;">
          <img v-else
            src="https://media.istockphoto.com/photos/cool-placeholder-for-your-picture-no-movie-screen-35mm-film-strip-picture-id1068817392?k=6&m=1068817392&s=170667a&w=0&h=hNRjLOOQ0p0iBsSsGZzi0lDWd9eCY0IK4jNQI5sVYVI=" />
      
        </div>
        <div class="flip-card-back">
          <h1>{{card.title ? card.title : card.name}}</h1>
          <!-- <p>Architect & Engineer</p>
          <p>We love that guy</p> -->
        </div>
      </div>
    </div>
    <!--   <img v-if="card.poster_path"
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
    <span v-else v-bind:class="'flag-icon flag-icon-' + card.original_language"></span> -->

    <!-- <img :src="'https://image.tmdb.org/t/p/w342' + card.poster_path"> -->
  <br />
  </li>

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
  border: 1px solid #f1f1f1;
  //perspective: 1000px; /* Remove this if you don't want the 3D effect */
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
.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
}

/* Style the front side (fallback if image is missing) */
.flip-card-front {
  background-color: #bbb;
  color: black;
}

/* Style the back side */
.flip-card-back {
  background-color: black;
  color: white;
  transform: rotateY(180deg);
}


</style>