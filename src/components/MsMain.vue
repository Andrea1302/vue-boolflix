<template>
  <main>

  </main>
</template>

<script>
export default {
  name: 'MsMain',
  props :{
    serched: String
  },
  data() {
      return {
          filmCercato : ""
      }
  },
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    main {
        height: 90vh;
        background-color: rgb(26, 25, 25);
    }
</style>