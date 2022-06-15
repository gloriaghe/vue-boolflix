<template>

    <div class="cardFilm">
        <img class="imgProgramma" :src="'https://image.tmdb.org/t/p/w342/' + singleCard.backdrop_path"
            :alt="singleCard.title">
        <h2>Titolo: {{ singleCard.title }} </h2>
        <h3>Titolo originale: {{ singleCard.original_title }}</h3>
        <span>Lingua: {{ singleCard.original_language }}</span>
        <img class="flag" :src="flag(this.singleCard.original_language)" :alt="singleCard.original_language">
        <span>Voto: {{ singleCard.vote_average }}</span>
        <span>Voto da 1 a 5: {{ this.voto1a5 }}</span>
        <span v-html="voto()"></span>
        <font-awesome-icon icon="fa-regular fa-star" />

    </div>

</template>

<script>
export default {
    name: 'CardFilm',
    props: {
        singleCard: Object
    },
    data() {
        return {
            voto1a5: "",
            stelline: '<font-awesome-icon icon="fa-regular fa-star"/>',
            // stellinePiene: '<font-awesome-icon icon="fa-regular fa-star"/>'

        }
    },
    mounted() {
        this.voto()

    },
    methods: {
        flag(lingua) {
            if (lingua === "en" || lingua === "it" || lingua === "es" || lingua === "fr") {

                return require('../assets/flag/' + lingua + ".png")
            } else {
                return require('../assets/flag/all.png')
            }

        },
        voto() {
            this.voto1a5 = Math.ceil(this.singleCard.vote_average / 2)

            if (this.voto1a5 == "1") {
                return this.stelline;
            } else if (this.voto1a5 == "2") {
                return this.stelline;
            } else if (this.voto1a5 == "3") {
                return this.stelline;
            } else if (this.voto1a5 == "4") {
                return this.stelline;
            } else {
                return this.stelline;

            }
            // switch (Math.ceil(this.singleCard.vote_average / 2)) {
            //     case "1":
            //         return "f005" ;
            //     case "2":
            //         return "f005 f005";
            //     case "3":
            //         return "f005";
            //     case "4":
            //         return "f005";
            //     case "5":
            //         return "f005"

            // }
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
div {
    display: flex;
    flex-direction: column;

    .cardFilm {
        width: 20%;

        .imgProgramma {
            max-width: 90%;
            height: 250px;
            object-fit: cover;
            object-position: center;
        }

        .flag {
            width: 10%;
        }

    }
}
</style>