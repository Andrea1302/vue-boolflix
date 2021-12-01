<template>
  <main>
    <div id="containerCards">
      <Card
        :ArrayTrovato="filmSearched"
      />

    </div>
  </main>
</template>

<script>
// import axios from "axios";
import Card from "./Card.vue"

export default {
  name: 'MsMain',
  components: {
    Card,
  },
  props : {
    filmSearched: Array
  },
  data() {
      return {
        ricerca: "",
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

</style>