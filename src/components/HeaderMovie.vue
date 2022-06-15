<template>
  <header>
    <img src="../assets/logo.png" alt="Logo Netflix">
    <div>
      <input type="text" placeholder="Cosa vuoi vedere?" v-model="inputCerca"
        @keyup.enter="$emit('search', inputCerca)">
      <button @click="$emit('search', inputCerca)">Cerca</button>
      <!-- <button @click="canc">Annulla ricerca</button> -->
    </div>
  </header>

</template>

<script>
export default {
  name: 'HeaderMovie',
  props: {

  },
  data() {
    return {
      inputCerca: "",
    }
  },
  methods: {
    canc() {
      this.inputCerca = ""
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
header {
  background-color: #0f0f0f;
  width: 100%;
  height: 80px;
  display: flex;
  justify-content: space-between;
  align-items: center;

  img {
    height: 80%;
    margin-left: 5%;
  }

  div {
    margin-right: 5%;

  }
}
</style>
