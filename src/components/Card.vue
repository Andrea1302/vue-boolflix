<template>
  <main>
    <div id="containerCards">
      <div class="card" v-for="film, i in ArrayTrovato" :key="i" >
        <img id="img_principale" :src="getImage(film)" alt="img">
        <div id="info">
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
            LINGUA : <img v-if="film.original_language === 'en' || film.original_language === 'it' " class="bandiera" :src="getLanguageImage(film)" alt="nazione">
          </div>
          <div class="sezioni">
            VOTO : {{film.vote_average}}
          </div>
        </div>
       
      </div>

    </div>
  </main>
</template>

<script>
// import axios from "axios";

export default {
  name: 'MsCard',
  props : {
    ArrayTrovato: Array
  },
  data() {
      return {
        ricerca: "",
        pathImage: "https://image.tmdb.org/t/p/w342/"
      }
  },
  created(){
  },
  methods : {
    getLanguageImage(element){
      if (element.original_language === 'en'){
        return "https://www.oltrevela.com/media/catalog/product/cache/2/small_image/600x600/9df78eab33525d08d6e5fb8d27136e95/3/4/3468fni/adria-bandiere-pcg-fn5252302-bandiera-inghilterra-20.png"
      } else if (element.original_language === 'it'){
        return "https://upload.wikimedia.org/wikipedia/commons/c/ca/Bandiera_italiana_foto.svg"
      } 
    },
    getImage(element){
      if (element.poster_path !== null) {
        return `https://image.tmdb.org/t/p/w342${element.poster_path}`
      } else  if (element.poster_path === null){
        return `https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQNQn862ehpJA_5eh3gI8SzbX47lf3zKv5S5g&usqp=CAU`
      }
      }
      
  }
  
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped  lang="scss">
    #containerCards{
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
      padding: 30px;
      width: 100%;
    }
    #img_principale{
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .card{
      // display: none;
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
        #info{
          display: none;
        }
    }
    .sezioni{
      margin: 10px 0
    }

// hover
.card:hover #img_principale{
  display: none;
}
.card:hover #info{
  display: block;
}

  // mediaquery
    @media all and ( max-width:992px) {
      .card{
        width: 30%;
      }
    }
    @media all and ( max-width:768px) {
      .card{
        width: 40%;
      }
    }
    @media all and ( max-width:576px) {
      .card{
        width: 100%;
      }
    }
</style>