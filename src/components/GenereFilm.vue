<template>
    <select name="Genere" v-model="inputGenre" @change="$emit('search', inputGenre)">
        <option disabled value="">Seleziona genere Film:</option>
        <option value="ALL">Tutti</option>
        <option v-for="(genreSingle, i) in genereDiverso" :key="i" :value="genreSingle">
            {{ genreSingle }}
        </option>

    </select>
</template>

<script>
export default {
    name: 'GenereFilm',
    props: {
        genre: Array

    },
    data() {
        return {
            inputGenre: "",
            genereDiverso: [],
        }
    },
    mounted() {
        // console.log("fuck", this.genre)
        // this.genre.forEach((element) => {
        
        //     console.log(element.name);
        //     if (!this.genereDiverso.includes(element.name)) {
        //         this.genereDiverso.push(element.name);

        //         console.log(this.genereDiverso)
                
        //     }
        // })
    }
    
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
select{
    display: block;
}
</style>