<template>
  <div id="app">
    <HeaderMovie @search="searchMovie" />

    <main>
      <div>
        <div v-if="loadingCard" id="loadCard">Sto cercando....</div>
        <div v-else class="cards">
          <GenereFilm @search="searchGenere"  /> <br>
          <H2 v-if="title">FILM</H2>
          <CardFilm v-for="(element, i) in movieCard" :key="i" :singleCard="element" />
          <GenereTV /> <br>
          <h2 v-if="title">TELEFILM</h2>
          <CardTV v-for="element in movieTVCard" :key="element.id" :singleCard="element" />
        </div>

      </div>
    </main>

  </div>
</template>

<script>
import axios from "axios";
import HeaderMovie from './components/HeaderMovie.vue'
import CardFilm from './components/CardFilm.vue';
import CardTV from './components/CardTV.vue';
import GenereFilm from "./components/GenereFilm.vue";
import GenereTV from "./components/GenereTV.vue";


export default {
  name: 'App',
  components: {
    HeaderMovie,
    CardFilm,
    CardTV,
    GenereFilm,
    GenereTV,
    
  },
  data() {
    return {
      apiUrlMovie: "https://api.themoviedb.org/3/search/movie?api_key=65f992091f5fb4cada3e4991ff084ab7&language=it-IT&query=",
      apiUrlTV: "https://api.themoviedb.org/3/search/tv?api_key=65f992091f5fb4cada3e4991ff084ab7&language=en-US&include_adult=false&query=",
      apiGenereFilm: "https://api.themoviedb.org/3/genre/movie/list?api_key=65f992091f5fb4cada3e4991ff084ab7&language=it-IT",
      apiGenereTV: "https://api.themoviedb.org/3/genre/tv/list?api_key=65f992091f5fb4cada3e4991ff084ab7&language=it-IT",
      movieTotal: {},
      movieCard: [],
      movieTVTotal: {},
      movieTVCard: [],
      userFilm: "",
      loadingCard: false,
      title: false,
      //genere
      genereFilm: [],
      genereTV: [],
      userGenre: "",
      

    }
  },
  created() {
    this.getGenere(this.apiGenereFilm, this.genereFilm);
    this.getGenere(this.apiGenereTV, this.genereTV);
    // this.pushGenre()
  },
  methods: {
    //genere
    searchGenere(genreuser) {
      this.userGenre = genreuser;
      console.log(genreuser)
    },
    getMovie(API) {

      this.loadingCard = true;

      axios.get(API + this.userFilm)
        .then((result) => {
          this.movieTotal = result.data;
          this.movieCard = this.movieTotal.results;
          console.log(this.movieCard);

          this.loadingCard = false;
          this.title = true;
        })
        //segnala errori api
        .catch((error) => {
          console.log("Errore", error);
        })
    },
    getTv(API) {

      axios.get(API + this.userFilm)
        .then((result) => {
          this.movieTVTotal = result.data;
          this.movieTVCard = this.movieTVTotal.results;
          console.log(this.movieTVCard);
        })
        //segnala errori api
        .catch((error) => {
          console.log("Errore", error);
        })
    },

    searchMovie(filmUser) {
      this.userFilm = filmUser
      console.log(this.userFilm)
      this.getMovie(this.apiUrlMovie)
      this.getTv(this.apiUrlTV)
    },

    getGenere(API, dovePUSHO) {
      axios.get(API)
        .then((result) => {
          dovePUSHO = result.data;
          console.log(dovePUSHO);

        })
        //segnala errori api
        .catch((error) => {
          console.log("Errore", error);
        });


    },
    

  },

}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: white;
  background-color: #128DA6;
  width: 100%;
  height: 100vh;


  main {

    height: calc(100vh - 140px);
    overflow: auto;

    #loadCard {
      margin-top: 30px;
      font-size: 30px;
    }

    .cards {
      display: flex;
      flex-wrap: wrap;
      flex-basis: 30%;
      margin-right: 30px;

      padding: 0 10%;
      padding-top: 40px;

      h2 {
        width: 100%;
        margin-bottom: 25px;
        margin-top: 35px;
        font-size: 30px;
      }
    }
  }
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style> 



