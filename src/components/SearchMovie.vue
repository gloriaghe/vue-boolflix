<template>
  
    <form>
        <input type="text" placeholder="Cosa vuoi vedere?" v-model="inputCerca" @input="$emit('search', inputCerca)">
        <button>Cerca</button>
    </form>
 
</template>

<script>
export default {
  name: 'SearchMovie',
  props: {
    
  },
  data(){
    return {
        inputCerca: "",
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
form{
    
}
</style>
