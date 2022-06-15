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


<template>
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
</style> 
