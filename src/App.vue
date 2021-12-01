<template>
  <div id="app">
    <header>
      <!-- Navbar ricerca  -->
      <MsNavbar
        @ricercaGenerata="filmSearched"
      />

    </header>

    <!-- main  -->
    <MsMain
      :filmSearched="ricercaGenerataApi"
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
      ricercaGenerataApi : []
    }
  },
  methods : {
    filmSearched(arrayRicercaApi){
      this.ricercaGenerataApi = arrayRicercaApi;
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
  color: #2c3e50;
  // height: 100vh;

}
</style>
