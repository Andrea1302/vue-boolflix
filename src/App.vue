<template>
  <div id="app">
    <header>
      <!-- Navbar ricerca  -->
      <MsNavbar
        @ricerca="filmSearched"
      />

    </header>

    <!-- main  -->
    <MsMain
      serched:filmCercato
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
      filmCercato : ""
    }
  },
  methods : {
    filmSearched(film){
      this.filmCercato = film
      // console.log(this.filmCercato);
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
