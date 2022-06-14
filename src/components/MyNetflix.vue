<template>
    <div class="">
        <SearchMovie />
    </div>
</template>

<script>
import axios from "axios";
import SearchMovie from './SearchMovie.vue';

export default {
    name: "MyNetflix",
    props: {},
    components: {
        SearchMovie,
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
        this.getMovie(this.apiUrl)
    },
    methods: {
        getMovie(API){
            axios.get(API)
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
    }
}
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
div {

}
</style>
