<template>
  <header>
    <img src="../assets/logo.png" alt="Logo Netflix">
    <div>
      <input type="text" placeholder="Cosa vuoi vedere?" v-model="inputCerca"
        @keyup.enter="$emit('search', inputCerca)">
      <button @click="$emit('search', inputCerca)">Cerca</button>
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
  },
  mounted() {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
header {
  background-color: #0B5766;
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

    input{
      height: 30px;
      background-color: #16AFCC;
      border: #16AFCC;
      color: white;
      padding-left: 20px;
      font-weight: bold;
    }

    button{
      background-color: #128DA6;
      border: none;
      padding: 7px 20px;
      color: white;
      border-radius: 20px;
    }
  }
}
</style>
