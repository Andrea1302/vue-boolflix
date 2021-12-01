<template>
  <nav>
    <div id="titolo">
        BOOLFLIX
    </div>
    <input type="text" placeholder="Ricerca il tuo film" v-model="ricercaFilm" @keyup.enter="invio">
  </nav>
</template>

<script>
import axios from "axios"
export default {
  name: 'MsNavbar',
  data() {
      return {
          ricercaFilm : "",
      }
  },
  methods : {
      invio(){
        //   this.$emit("ricerca",this.ricercaFilm)
        axios
        .get(`https://api.themoviedb.org/3/search/movie?api_key=48ceee017a943196a6809d6419385050&query=${this.ricercaFilm}&language=it=IT`)
        .then((res)=>{
            this.$emit("ricercaGenerata",res.data.results)
        })
        
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


    @media all and ( max-width:576px) {
     nav {
       flex-direction: column;
     }
    }
</style>
