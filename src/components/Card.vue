<template>
  <main>
    <div id="containerCards">

      <!-- Sezione film  -->
      <div class="card" v-for="film, i in ArrayTrovato" :key="'film'+i" >
        <!-- Immagine di background  card -->
        <img id="img_principale" :src="getImage(film)" alt="img">

        <!-- on hover  -->
        <div id="info">
           <!-- titolo  -->
          <div class="sezioni">
              <span class="details">TITOLO :</span>  <span>{{film.title}}</span>
          </div>
          <!-- titolo originale  -->
          <div class="sezioni">
            <span class="details">TITOLO ORIGINALE :</span>  <span>{{film.original_title}}</span>
          </div>

          <!-- LINGUA  -->
          <div class="sezioni">
            <span class="details">LINGUA :</span>  <img v-if="getLanguageImage(film) !== 'notfound'"  class="bandiera" :src="getLanguageImage(film)" :alt="film.original_language"> <span v-if="getLanguageImage(film) === 'notfound'">{{film.original_language}}</span>
          </div>

          <!-- Voto  -->
          <div class="sezioni" v-if="film.vote_average > 0">
            <span class="details">VOTO :</span>  <i class="fas fa-star" :class="getStarVote(film) >=1 ? 'active' : ''"></i> <i class="fas fa-star" :class="getStarVote(film) >=2 ? 'active' : ''"></i> <i class="fas fa-star" :class="getStarVote(film) >=3 ? 'active' : ''" ></i> <i class="fas fa-star" :class="getStarVote(film) >=4 ? 'active' : ''"></i> <i class="fas fa-star" :class="getStarVote(film) >=5 ? 'active' : ''"></i> {{film.vote_average}}
          </div>

          <!-- Overview -->
          <div class="sezioni" id="overview">
            <span class="details">Overview :</span>  {{film.overview}}
          </div>
        </div>
       
      </div>
      

      <!--sezione Serie  -->
      <div class="card" v-for="film, i in ArrayTrovatoSerie" :key="'serie'+i" >
        <!-- Immagine di background  card -->
        <img id="img_principale" :src="getImage(film)" alt="img">

        <!-- on hover  -->
        <div id="info">
           <!-- titolo  -->
          <div class="sezioni">
              TITOLO : <span>{{film.name}}</span>
          </div>
          <!-- titolo originale  -->
          <div class="sezioni">
            TITOLO ORIGINALE : <span>{{film.original_name}}</span>
          </div>

          <!-- LINGUA  -->
          <div class="sezioni">
            LINGUA : <img v-if="getLanguageImage(film) !== 'notfound'"  class="bandiera" :src="getLanguageImage(film)" :alt="film.original_language"> <span v-if="getLanguageImage(film) === 'notfound'">{{film.original_language}}</span>
          </div>

          <!-- Voto  -->
          <div class="sezioni" v-if="film.vote_average > 0">
            VOTO : <i class="fas fa-star" :class="getStarVote(film) >=1 ? 'active' : ''"></i> <i class="fas fa-star" :class="getStarVote(film) >=2 ? 'active' : ''"></i> <i class="fas fa-star" :class="getStarVote(film) >=3 ? 'active' : ''" ></i> <i class="fas fa-star" :class="getStarVote(film) >=4 ? 'active' : ''"></i> <i class="fas fa-star" :class="getStarVote(film) >=5 ? 'active' : ''"></i> {{film.vote_average}}
          </div>

          <!-- Overview -->
          <div class="sezioni" id="overview">
            Overview : {{film.overview}}
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
    ArrayTrovato: Array,
    ArrayTrovatoSerie: Array
  },
  data() {
      return {
        ricerca: "io",
        pathImage: "https://image.tmdb.org/t/p/w342/",
        StellinaVoto : ""
      }
  },
  created(){
  
  },
  computed : {
    
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
    },
    getStarVote(element){
      let voto = Math.round((element.vote_average / 2) )
      return voto
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
      height: 426px;
      overflow: scroll;
      color: white;
      font-weight: bold;
      background-color: black;
      box-shadow: 5px 5px 14px 3px black;
        .bandiera{
          width: 20px;
        }
        #info{
          display: none;
        }
        
    }
    // star active 
    .active{
      color: yellow;
    }

    // Sezioni on hover 
    .sezioni{
      margin: 10px 0;
      .details{
        color: red;
      }
    }

// hover
.card:hover{
  padding: 10px;
  box-shadow: none;
}
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