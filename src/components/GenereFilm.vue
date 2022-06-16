<template>
    <select name="Genere" v-model="inputGenre" @change="$emit('search', inputGenre)">
        <option disabled value="">Genere Film:</option>
        <option value="ALL">Tutti</option>
        <option v-for="genere in genereVari" :key="genere.id">
            {{ genere.id }}
            <span>{{ genere.name }}</span>
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

        this.getGenere();
       
    },
    methods: {

        getGenere() {
            axios.get(this.apiGenereFilm)
                .then((result) => {
                    this.genereApi = result.data;
                    this.genereVari = this.genereApi.genres

                    
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