<template>
  <main>
    <div id="containerCards">
      <div class="card" v-for="film, i in ArrayTrovato" :key="i" >
        <!-- Immagine di background  card -->
        <img id="img_principale" :src="getImage(film)" alt="img">

        <!-- on hover  -->
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
            LINGUA : <img v-if="getLanguageImage(film) !== 'notfound'"  class="bandiera" :src="getLanguageImage(film)" :alt="film.original_language"> <span v-if="getLanguageImage(film) === 'notfound'">{{film.original_language}}</span>
          </div>

          <!-- Voto  -->
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
        pathImage: "https://image.tmdb.org/t/p/w342/",
      }
  },
  created(){
  },
  methods : {

    // per stampare immagine bandiera trovata al posto del semplice testo 
    getLanguageImage(element){
      if (element.original_language === 'en'){
        return "https://www.oltrevela.com/media/catalog/product/cache/2/small_image/600x600/9df78eab33525d08d6e5fb8d27136e95/3/4/3468fni/adria-bandiere-pcg-fn5252302-bandiera-inghilterra-20.png"
      } else if (element.original_language === 'it'){
        return "https://upload.wikimedia.org/wikipedia/commons/c/ca/Bandiera_italiana_foto.svg"
      } else if (element.original_language === 'ja'){
        return "https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Flag_of_Japan.svg/280px-Flag_of_Japan.svg.png"
      } else if (element.original_language === 'tl'){
        return "https://upload.wikimedia.org/wikipedia/commons/thumb/2/26/Flag_of_East_Timor.svg/2880px-Flag_of_East_Timor.svg.png"
      }  else if (element.original_language === 'es'){
        return "https://d1bvpoagx8hqbg.cloudfront.net/originals/la-bandiera-della-spagna-d9233b06138fb2138a46f6e4b6d3d992.jpg"
      }  else if (element.original_language === 'fr'){
        return "https://upload.wikimedia.org/wikipedia/commons/thumb/3/3a/Flag_of_France_%281794%E2%80%931815%2C_1830%E2%80%931958%29.svg/280px-Flag_of_France_%281794%E2%80%931815%2C_1830%E2%80%931958%29.svg.png"
      } else{
        return "notfound"

      }

    },
    // Per stampare immagine di background card 
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
      flex-wrap: wrap;
      padding: 30px;
      width: 100%;
    }
    #img_principale{
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    // Card trovata dopo la ricerca 
    .card{
      width: 21%;
      margin: 20px auto;
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

    // Sezioni on hover 
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


    // Desktop
    @media all and ( max-width:992px) {
      .card{
        width: 30%;
      }
    }

    // Tablet 
    @media all and ( max-width:768px) {
      .card{
        width: 40%;
      }
    }

    // Smartphone 
    @media all and ( max-width:576px) {
      .card{
        width: 100%;
      }
    }
</style>