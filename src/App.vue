<template>
  <div id="app">
    <HeaderMovie @search="searchMovie" />
    <main>
      <div class="cards">
        <h2>Film</h2>
        <CardFilm v-for="(element, i) in movieCard" :key="i" :singleCard="element" />
        <h2>Telefilm</h2>
        <CardTV v-for="element in movieTVCard" :key="element.id" :singleCard="element" />
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import HeaderMovie from './components/HeaderMovie.vue'
import CardFilm from './components/CardFilm.vue';
import CardTV from './components/CardTV.vue';

export default {
  name: 'App',
  components: {
    HeaderMovie,
    CardFilm,
    CardTV
  },
  data() {
    return {
      apiUrlMovie: "https://api.themoviedb.org/3/search/movie?api_key=65f992091f5fb4cada3e4991ff084ab7&language=it-IT&query=",
      apiUrlTV: "https://api.themoviedb.org/3/search/tv?api_key=65f992091f5fb4cada3e4991ff084ab7&language=en-US&include_adult=false&query=",
      movieTotal: {},
      movieCard: [],
      movieTVTotal: {},
      movieTVCard: [],
      userFilm: "",
    }
  },
  methods: {

    getMovie(API) {
      axios.get(API + this.userFilm)
        .then((result) => {
          this.movieTotal = result.data;
          this.movieCard = this.movieTotal.results;
          console.log(this.movieCard);
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
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: white;
  background-color: #1c2b3b;
  width: 100%;
  height: 100vh;
 

  main {
    .cards {
      display: flex;
      flex-wrap: wrap;
      flex-basis: 30%;
      margin-right: 30px;
      height: calc(100vh - 80px);
      overflow: auto;
      padding: 0 10%;
      padding-top: 40px;

      h2{
        width: 100%;
      }
    }
  }
}

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style> 



<!-- <template>
  <div id="app">
    <HeaderMovie @search="searchMovie"/>
    <MyNetflix/>
  </div>
</template>

<script>
import MyNetflix from './components/MyNetflix.vue';
import HeaderMovie from './components/HeaderMovie.vue';

// import axios from "axios";

export default {
  name: 'App',
  components: {
    MyNetflix,
    HeaderMovie
  },
  data() {
        return {
           
            userFilm: "",
            UsersProps: ""
        }
    },
    methods:{

     
          searchMovie(filmUser) {
              this.userFilm = filmUser
              this.userFilm = this.UsersProps
              // console.log(this.userFilm)
              // this.getMovie(this.apiUrlMovie)
              // this.getTv(this.apiUrlTV)
          },
    }

}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style> -->


<!-- <template>
  <div id="app">
    <HeaderMovie/>
    <MyNetflix/>
  </div>
</template>

<script>
import MyNetflix from './components/MyNetflix.vue'
import HeaderMovie from './components/HeaderMovie.vue'


export default {
  name: 'App',
  components: {
    MyNetflix,
    HeaderMovie
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>  -->
