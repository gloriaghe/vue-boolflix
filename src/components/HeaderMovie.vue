<template>
  <header>

    <div>
        <input type="text" placeholder="Cosa vuoi vedere?" v-model="inputCerca" @keyup.enter="$emit('search', inputCerca)">
        <button  @click="$emit('search', inputCerca)">Cerca</button >
    </div>
  </header>
 
</template>

<script>
export default {
  name: 'HeaderMovie',
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
header{
  background-color: #0f0f0f;
  width: 100%;
  height: 80px;
}
</style>
