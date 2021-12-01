<template>
  <main>
    <div id="containerCards">
      <div class="card"  v-for="film, i in filmSearched" :key="i">
        {{film.title}}
      </div>

    </div>
  </main>
</template>

<script>
// import axios from "axios";

export default {
  name: 'MsMain',
  props : {
    filmSearched: Array
  },
  data() {
      return {
        ricerca: ""
      }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    main {
        height: 90vh;
        background-color: rgb(26, 25, 25);
    }
    #containerCards{
      display: flex;
      flex-wrap: wrap;
      padding: 30px;
    }
    .card{
      width: 24%;
      margin: 20px 0;
      min-height: 100px;
      // debug
      background-color: blue;
      border: 1px solid black;

    }
</style>