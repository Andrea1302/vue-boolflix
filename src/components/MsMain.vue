<template>

<!-- Contenitore cards  -->
  <main>
      <Card
        :ArrayTrovato="filmSearched"
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
    filmSearched: Array
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
        background-color: rgb(26, 25, 25);
        overflow: scroll;
    }

</style>