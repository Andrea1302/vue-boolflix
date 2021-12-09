<template>

<!-- Contenitore cards  -->
  <main>
      <Card
        :ArrayTrovatoFilm="filmSearched"
        :ArrayTrovatoSerie="serieSearched"
        :activeRicerca="RicercaFatta"
        :RicercaTopRated="RicercaTopRated"

      />
      <TopRatedCard
        :ArrayTopRated="iPiuVotati"
        :RicercaTopRated="RicercaTopRated"
      />
      
  </main>
  
</template>

<script>
// import axios from "axios";
import Card from "./Card.vue";
import TopRatedCard from "./TopRatedCard.vue"

export default {
  name: 'MsMain',
  components: {
    Card,
    TopRatedCard
  },
  props : {
    filmSearched: Array,
    serieSearched: Array,
    iPiuVotati:Array,
    RicercaFatta:Boolean,
    RicercaTopRated:Boolean
  },
  data() {
      return {
      }
  },
  methods : {
    check(){
      if ( this.RicercaFatta === true ){
        this.RicercaTopRated = false
      }
      if ( this.RicercaTopRated === true){
        this.RicercaFatta = false
      }
    },
    prova(){
      console.log("ricerca"+this.RicercaFatta);
      console.log("votati"+this.RicercaTopRated);
    }
  },
  
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