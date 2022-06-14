<template>
  
    <div class="cardFilm">
        <h2>Titolo: {{singleCard.title}} </h2>
        <h3>Titolo originale: {{singleCard.original_title}}</h3>
        <span>Lingua: {{singleCard.original_language}}</span>
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