<template>
  <main>
    <div id="containerCards">
    
      <div class="card"  v-for="film, i in filmSearched" :key="i">
        <!-- titolo  -->
        <div class="sezioni">
            TITOLO : {{film.title}}
        </div>
        <!-- titolo originale  -->
        <div class="sezioni">
          TITOLO ORIGINALE : {{film.original_title}}
        </div>

        <!-- LINGUA  -->
        <div class="sezioni">
          LINGUA : <img v-if="film.original_language === 'en' || film.original_language === 'it' " class="bandiera" :src="film.original_language === 'en' ? 'https://www.oltrevela.com/media/catalog/product/cache/2/small_image/600x600/9df78eab33525d08d6e5fb8d27136e95/3/4/3468fni/adria-bandiere-pcg-fn5252302-bandiera-inghilterra-20.png' : film.original_language === 'it' ?  'https://upload.wikimedia.org/wikipedia/commons/c/ca/Bandiera_italiana_foto.svg' :'' " alt="nazione">
        </div>
        <div class="sezioni">
          VOTO : {{film.vote_average}}
        </div>
      </div>

    </div>
  </main>
</template>

<script>
// import axios from "axios";

export default {
  name: 'MsMain',
  props : {
    filmSearched: Array
  },
  data() {
      return {
        ricerca: "",
        bandiera : ""
      }
  },
  computed : {
    nazione(){
      return this.filmSearched.forEach((element)=>{
        if (element.original_language === 'en'){
          return this.bandiera = "https://www.oltrevela.com/media/catalog/product/cache/2/small_image/600x600/9df78eab33525d08d6e5fb8d27136e95/3/4/3468fni/adria-bandiere-pcg-fn5252302-bandiera-inghilterra-20.png"
        }
      })
    }
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
    #containerCards{
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
      padding: 30px;
    }
    .card{
      width: 21%;
      margin: 20px 0;
      min-height: 500px;
      color: white;
      font-weight: bold;
      padding: 10px;
      background-color: black;
        .bandiera{
          width: 20px;

        }
    }
    .sezioni{
      margin: 10px 0
    }

</style>