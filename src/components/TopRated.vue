<template>
    <div id="top_rated" @click="top_rated">
        I più votati
    </div>
</template>

<script>
import axios from "axios"

export default {
  name: 'TopRated',
  components: {
    
  },
  props : {
  },
  data() {
      return {
        TopRated : []
      }
  },

  methods : {
      top_rated(){
          axios
          .get("https://api.themoviedb.org/3/movie/top_rated?api_key=48ceee017a943196a6809d6419385050&language=en-US&page=1")
          .then((res)=>{
              this.TopRated = res.data
          })
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style  lang="scss">

    #top_rated{
      padding: 5px 15px;
      border: 1px solid white;
      cursor: pointer;
      box-shadow: 0px 0px 5px 1px white;
    }

    
</style>