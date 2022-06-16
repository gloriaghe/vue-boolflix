<template>
  <select name="Genere" v-model="inputGenre" @change="$emit('search', inputGenre)">
    <option disabled value="">Genere TV:</option>
    <option value="ALL">Tutti</option>
    <option v-for="genreSingle in genereVariTV" :key="genreSingle.id">
      {{ genreSingle.name }}
    </option>

  </select>
</template>

<script>
import axios from "axios";

export default {
  name: 'GenereTV',
  props: {

  },
  data() {
    return {
      inputGenre: "",
      apiGenereTV: "https://api.themoviedb.org/3/genre/tv/list?api_key=65f992091f5fb4cada3e4991ff084ab7&language=it-IT",
      genereApiTV: {},
      genereVariTV: []
    }
  },
  created() {
    this.getGenere()
  },
  methods: {
    getGenere() {
      axios.get(this.apiGenereTV)
        .then((result) => {
          this.genereApiTV = result.data;
          this.genereVariTV = this.genereApiTV.genres

        })
        //segnala errori api
        .catch((error) => {
          console.log("Errore", error);
        });


    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>