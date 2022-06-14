<template>
  
    <div class="cardFilm">
        <h2>Titolo: {{singleCard.name}} </h2>
        <h3>Titolo originale: {{singleCard.original_name}}</h3>
        <span>Lingua: {{singleCard.original_language}}</span>
        <img :src="flag(this.singleCard.original_language)" :alt="singleCard.original_language">
        <span>Voto: {{singleCard.vote_average}}</span>
    </div>
 
</template>

<script>
export default {
  name: 'CardTV',
  props: {
    singleCard: Object
  },
  data(){
    return {
        myFlag: ""
    }
  },
  methods:{
    flag(lingua){
        
            this.myFlag = require('../assets/flag/' + lingua + ".png")
            console.log("LINK:", this.myFlag)
        
    }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
div{
    display: flex;
    flex-direction: column;
}
</style>