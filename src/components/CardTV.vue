<template>
  
    <div class="cardFilm">
        <img  class="imgProgramma" :src="'https://image.tmdb.org/t/p/w342/'+singleCard.poster_path" :alt="singleCard.name">
        <h2>Titolo: {{singleCard.name}} </h2>
        <h3>Titolo originale: {{singleCard.original_name}}</h3>
        <span>Lingua: {{singleCard.original_language}}</span>
        <img  class="flag" :src="flag(singleCard.original_language)" :alt="singleCard.original_language">
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
        
    }
  },
  methods:{
    flag(lingua){
           if(lingua === "en" || lingua === "it" || lingua === "es" || lingua === "fr" ){

               return require('../assets/flag/' + lingua + ".png")
           } else {
            return require('../assets/flag/all.png')
           }
        
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

        .flag{
            width: 10%;
        }
    }
}
</style>