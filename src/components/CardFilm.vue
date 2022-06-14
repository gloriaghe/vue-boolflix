<template>
  
    <div class="cardFilm">
        <img class="imgProgramma" :src="'https://image.tmdb.org/t/p/w342/'+singleCard.backdrop_path" :alt="singleCard.name">
        <h2>Titolo: {{singleCard.title}} </h2>
        <h3>Titolo originale: {{singleCard.original_title}}</h3>
        <span>Lingua: {{singleCard.original_language}}</span>
        <img :src="flag(this.singleCard.original_language)" :alt="singleCard.original_language">
        <span>Voto: {{singleCard.vote_average}}</span>
    </div>
 
</template>

<script>
export default {
  name: 'CardFilm',
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

    .cardFilm{
        width: 20%;
        
        .imgProgramma{
            max-width:80%
        }
    }
}
</style>