<template>
    <div id="appCerca">
         <HeaderMovie @search="searchMovie" /> 
        <div>
            <h1>Film</h1>
            <div class="cards">
                <CardFilm v-for="(element, i) in movieCard" :key="i" :singleCard="element" />
            </div>
            <h1 id="TV">TV</h1>
            <div class="cards">
                <CardTV v-for="element in movieTVCard" :key="element.id" :singleCard="element" />
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios";
import HeaderMovie from './HeaderMovie.vue';
import CardFilm from './CardFilm.vue';
import CardTV from './CardTV.vue';


export default {
    name: "MyNetflix",
    props: {},
    components: {
        HeaderMovie,
        CardFilm,
        CardTV,
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
    created() {
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#appCerca {

    .cards {
        display: flex;
        flex-wrap: wrap;
        flex-basis: 30%;
        margin-right: 30px;



    }
}
</style>


APP VECCHIA

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
