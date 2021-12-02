<template>
  <nav>
    <!-- Titolo  -->
    <div id="titolo">
        BOOLFLIX
    </div>

    <div id="container_generi">
        <div id="generiFilm" @click="ricercaGeneri">
          Generi Film
        </div>
        <div v-show="this.activeFilmGenre" class="generi_trovati">
          <div v-for="genere,i in generiFilm" :key="'genere'+i">
            
              <div class="genere_film_singolo"> 
                {{genere.name}}
              </div>
            
          </div>
            
        </div>
    </div>
    
    <!-- <div class="generiTrovati" v-for="genere,i in generiFilm" :key="'genere'+i">
      <div id="genere">
        {{genere.name}}
      </div>
    </div> -->
      
    
    <!-- Input ricerca film o serie tv -->
    <div id="search">
      <i class="fas fa-search" id="ricerca_icon" @click="ricerca"></i>
      <input class="input_ricerca" :class="active? 'active' : '' " type="text" placeholder="Ricerca il tuo film" v-model="ricercaFilm" @keyup.enter="invio">
    </div>
    
  </nav>
</template>

<script>
import axios from "axios"
export default {
  name: 'MsNavbar',
  data() {
      return {
          ricercaFilm : "",
          active : false,
          activeFilmGenre : false,
          generiFilm : []
      }
  },
  methods : {
      invio(){

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
      }
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
    // generi film 
    #container_generi{
      position: relative;
      display: flex;
      flex-direction: column;
    }
    #generiFilm{
      padding: 5px 15px;
      border: 1px solid white;
      cursor: pointer;
      box-shadow: 0px 0px 5px 1px white;
    }
    .generi_trovati{
      position: absolute;
      top:50px;
      padding: 30px;
      background-color: black;
      border: 2px solid white;
      box-shadow: 0px 0px 5px 1px white;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      width: 500px;
      .genere_film_singolo {
        min-width: 180px;
        margin: 10px 0;
        list-style: none;
        padding: 10px;
        cursor: pointer;
        box-shadow: 0px 1px 13px 1px red;
      }
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
