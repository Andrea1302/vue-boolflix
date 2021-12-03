<template>
    <div id="container_generi">
        <div id="generiFilm" @click="ricercaGeneri">
          Generi Film
        </div>
        <div v-show="this.activeFilmGenre" class="generi_trovati">
          <div v-for="genere,i in generiFilm" :key="'genere'+i">
            
              <div class="genere_film_singolo"> 
                {{genere.name}} {{i}}
              </div>
            
          </div>
            
        </div>
    </div>
</template>

<script>
import axios from "axios"

export default {
  name: 'Genre',
  components: {
    
  },
  props : {
  },
  data() {
      return {
        activeFilmGenre : false,
        generiFilm : []
      }
  },
  created(){
  },
  methods : {
      ricercaGeneri(){
        axios
        .get("https://api.themoviedb.org/3/genre/movie/list?api_key=48ceee017a943196a6809d6419385050&language=en-US")
        .then((res)=>{
          this.generiFilm = res.data.genres;
        })
          if (this.activeFilmGenre === false ){
          this.activeFilmGenre = true
        } else if ( this.activeFilmGenre === true ) {
          this.activeFilmGenre = false
        }
      },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style  lang="scss">
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
    
</style>