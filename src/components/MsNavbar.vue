<template>
  <nav>
    <div id="titolo">
        BOOLFLIX
    </div>
    <input type="text" placeholder="Ricerca il tuo film" v-model="ricercaFilm" @keyup.enter="invio">
  </nav>
</template>

<script>
export default {
  name: 'MsNavbar',
  data() {
      return {
          ricercaFilm : "",
      }
  },
  methods : {
      invio(){
          this.$emit("ricerca",this.ricercaFilm)
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
        height: 10vh;
        #titolo{
            font-size: 30px;
            color: red;
        }
    }
</style>
