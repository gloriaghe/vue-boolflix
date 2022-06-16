<template>
    <select name="Genere" v-model="inputGenre" @change="$emit('search', inputGenre)">
        <option disabled value="">Seleziona genere Film:</option>
        <option value="ALL">Tutti</option>
        <option v-for="genere in genereVari" :key="genere.id">
            {{ genere.name }}
        </option>
    </select>
</template>

<script>
import axios from "axios";


export default {
    name: 'GenereFilm',
    props: {

    },
    data() {
        return {
            inputGenre: "",
            apiGenereFilm: "https://api.themoviedb.org/3/genre/movie/list?api_key=65f992091f5fb4cada3e4991ff084ab7&language=it-IT",
            genereApi: {},
            genereVari: []
        }
    },
    created() {

        this.getGenere(this.apiGenereFilm, this.genereApi, this.genereVari);
       
    },
    methods: {

        getGenere(API, dovePUSHO, dovepusho2 ) {
            axios.get(API)
                .then((result) => {
                    dovePUSHO = result.data;
                    console.log(dovePUSHO)
                    dovepusho2 = dovePUSHO.genres

                    console.log("qui c'è?", dovepusho2);
                    
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
select {}
</style>