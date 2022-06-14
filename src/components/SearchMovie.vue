<template>
  
    <div>
        <input type="text" placeholder="Cosa vuoi vedere?" v-model="inputCerca" @keyup.enter="$emit('search', inputCerca)">
        <button  @click="$emit('search', inputCerca)">Cerca</button >
    </div>
 
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

</style>
