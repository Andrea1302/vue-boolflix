<template>
  <nav>
    <!-- Titolo  -->
    <div id="titolo">
        BOOLFLIX
    </div>
    <Genres/>
    <TopRated 
      @clickTopRated="clicked"
      @topRatedArray="topRatedArray"/>
    <!-- Input ricerca film o serie tv -->
    <div id="search">
      <i class="fas fa-search" id="ricerca_icon" @click="ricerca"></i>
      <input class="input_ricerca" :class="active? 'active' : '' " type="text" placeholder="Ricerca il tuo film" v-model="ricercaFilm" @keyup.enter="invio">
    </div>
    
  </nav>
</template>

<script>
import axios from "axios"
import Genres from "./GeneriSerie.vue";
import TopRated from "./TopRated.vue"
export default {
  name: 'MsNavbar',
  components :{
    Genres,
    TopRated
  },
  data() {
      return {
          ricercaFilm : "",
          active : false,
          activeFilmGenre : false,
          generiFilm : [],
          topRateds : [],
          activeSearch : false,
      }
  },
  methods : {
      invio(){
        this.activeSearch = true;
        this.$emit("activeSearch",this.activeSearch)
        // chiamata axios Film 
        axios
        .get(`https://api.themoviedb.org/3/search/movie?api_key=48ceee017a943196a6809d6419385050&query=${this.ricercaFilm}&language=it=IT`)
        .then((res)=>{ 
              this.$emit("ricercaGenerata",res.data.results)

        }) 

        // chiamata axios Serie tv 
        axios
        .get(`https://api.themoviedb.org/3/search/tv?api_key=48ceee017a943196a6809d6419385050&query=${this.ricercaFilm}&language=it=IT`)
        .then((res)=>{
            
              this.$emit("ricercaGenerataSerie",res.data.results)
            
        })
        this.ricercaFilm = ""
        
      },
      ricerca(){
        if (this.active === false ){
          this.active = true
        } else if ( this.active === true ) {
          this.active = false
        }
      },
      ricercaGeneri(){
        axios
        .get("https://api.themoviedb.org/3/genre/movie/list?api_key=48ceee017a943196a6809d6419385050&language=en-US")
        .then((res)=>{
          console.log(res.data.genres);
          this.generiFilm = res.data.genres;
        })
          if (this.activeFilmGenre === false ){
          this.activeFilmGenre = true
        } else if ( this.activeFilmGenre === true ) {
          this.activeFilmGenre = false
        }
      },
      topRatedArray(array){
        this.$emit('topRatedArray',array)
      },
      clicked(valore){
        this.$emit("checkClick",valore);
      },
      
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    nav{
        display: flex;
        justify-content: space-between;
        padding: 20px;
        align-items: center;
        background-color: black;
        min-height: 10vh;
        #titolo{
            font-size: 30px;
            color: red;
        }
    }
    .input_ricerca{
      display: none;
    }
    .active{
      display: block;
    }
    #ricerca_icon{
      font-size: 30px;
      cursor: pointer;
      color: white;
      margin-right: 20px;
    }
    #search{
      display: flex;
    }
    // Smartphone 
    @media all and ( max-width:576px) {
     nav {
       flex-direction: column;
     }
    }
</style>
