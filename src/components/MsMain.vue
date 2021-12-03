<template>

<!-- Contenitore cards  -->
  <main>
      <Card
        :ArrayTrovatoFilm="filmSearched"
        :ArrayTrovatoSerie="serieSearched"
      />

  </main>
</template>

<script>
// import axios from "axios";
import Card from "./Card.vue"

export default {
  name: 'MsMain',
  components: {
    Card,
  },
  props : {
    filmSearched: Array,
    serieSearched: Array,
  },
  data() {
      return {
        ricerca: "",
      }
  },
  created(){
  },
  methods : {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style  lang="scss">
    main {
        height: 90vh;
        background-color: rgba(26, 25, 25, 0.493);
        overflow: scroll;
    }

</style>