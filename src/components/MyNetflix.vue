<template>
    <div id="appCerca">
        <SearchMovie  @search="searchMovie"/>
        <div id="cards">
            <CardFilm v-for="(element, i) in movieCard" :key="i" :singleCard="element"/>
        </div>
    </div>
</template>

<script>
import axios from "axios";
import SearchMovie from './SearchMovie.vue';
import CardFilm from './CardFilm.vue';

export default {
    name: "MyNetflix",
    props: {},
    components: {
        SearchMovie,
        CardFilm,
    },
    data() {
        return {
            apiUrl: "https://api.themoviedb.org/3/search/movie?api_key=65f992091f5fb4cada3e4991ff084ab7&language=it-IT&query=",
            movieTotal:{},
            movieCard: [],
            userFilm:"",
        }
    },
    created(){
    },
    methods: {
        getMovie(API){
            axios.get(API+this.userFilm)
        .then((result) => {
            this.movieTotal = result.data;
            this.movieCard = this.movieTotal.results
            console.log(this.movieCard)
        })
          //segnala errori api
        .catch((error) => {
          console.log("Errore", error);
        })
    },
    searchMovie(filmUser){
        this.userFilm= filmUser
        console.log(this.userFilm)
        this.getMovie(this.apiUrl)
    }
}
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#appCerca {
 
 #cards{
    display: flex;
    flex-wrap: wrap;
    flex-basis: 30%;
    margin-right: 30px;
 }
}
</style>
