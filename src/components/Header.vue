<template>
  <div class="header">
    
    <div class="logo">
        <h1>Boolflix</h1>
    </div>

    <div class="search-box">
      <input type="text" placeholder="Search" v-model="inputText" @keyup.enter="$emit('search','inputText')" />
      </div>

  </div>
</template>

<script>
  export default {
    name: 'Header',
    data() {
      return {
        inputText : ' ',
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  @import '~fontsource-bebas-neue/latin-ext.css';
  .header {
    background: black;
    display: flex;
    justify-content: space-between;
    align-items: center;
    .logo{
      padding: 0 20px;
    h1 {
      font-family: 'Bebas Neue', cursive;
      text-transform: uppercase;
      color:red;
      font-weight: 800;
      padding: em(20);
    }
    }
    

  }

</style>