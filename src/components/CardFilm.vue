<template>

    <div class="cardFilm">
        <img class="imgProgramma" :src="'https://image.tmdb.org/t/p/w342/' + singleCard.poster_path"
            :alt="singleCard.title">
        <div class="textCard">
            <h3><strong>Titolo:</strong> {{ singleCard.title }} </h3>
            <h3>Titolo originale: {{ singleCard.original_title }}</h3>
            <span>Lingua: {{ singleCard.original_language }}</span>
            <img class="flag" :src="flag(this.singleCard.original_language)" :alt="singleCard.original_language">
            <div class="voto">
                <span><strong>Voto: </strong></span>
                <span class="stelle">
                    <font-awesome-icon v-for="(element, i) in voto()" :key="i + 'n'" icon="fa-solid fa-star" />
                    <font-awesome-icon v-for="(element, i) in voto5()" :key="i" icon="fa-regular fa-star" />
                </span>
            </div>
            <span>{{ singleCard.overview }}</span>
        </div>
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
            this.voto1a5 = Math.ceil(this.singleCard.vote_average / 2);
            return this.voto1a5
        },
        voto5() {
            return (5 - this.voto1a5)
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../assets/card.scss';
</style>