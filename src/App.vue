<template>
  <div id="app">
    <header>
      <!-- Navbar ricerca  -->
      <MsNavbar
        @ricercaGenerata="filmSearched"
        @ricercaGenerataSerie="filmSearchedSeries"
        @topRatedArray="topRatedArray"
        @activeSearch="activeSearch"
        @checkClick="ActiveTopRated"
      />

    </header>

    <!-- main  -->
    <MsMain
      :filmSearched="ricercaGenerataApi"
      :serieSearched="ricercaGenerataApiSeries"
      :iPiuVotati="topRateds"
      :RicercaFatta="RicercaCheck"
      :RicercaTopRated="ricercaTopGeneri"
    />

    
  </div>
</template>

<script>
import MsNavbar from './components/MsNavbar.vue';
import MsMain from './components/MsMain.vue';



export default {
  name: 'App',
  components: {
    MsNavbar,
    MsMain,
  },
  data(){
    return {
      filmCercato : "",
      ricercaGenerataApi : [],
      ricercaGenerataApiSeries : [],
      topRateds: [],
      RicercaCheck : "",
      ricercaTopGeneri : ""
    }
  },
  methods : {
    filmSearched(arrayRicercaApi){
      this.ricercaGenerataApi = arrayRicercaApi;
    },
    filmSearchedSeries(arrayRicercaApi){
      this.ricercaGenerataApiSeries = arrayRicercaApi;
    },
    topRatedArray(array){
      this.topRateds = array
    },
    activeSearch(valore){
      this.RicercaCheck = valore
      
    },
    ActiveTopRated(valore){
      this.ricercaTopGeneri = valore
    }
    
  }
}
</script>

<style lang="scss">
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body{
  height: 100vh;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: white;
  background-image: url(https://assets.nflxext.com/ffe/siteui/vlv3/23c72870-12c8-4682-9f55-337a083ccfa7/5ae78ee3-d067-4e34-9654-c218ec43e607/IT-it-20211129-popsignuptwoweeks-perspective_alpha_website_large.jpg);

}
</style>
