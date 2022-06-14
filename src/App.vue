<template>
  <div id="app">
    <MyNetflix/>
  </div>
</template>

<script>
import MyNetflix from './components/MyNetflix.vue'

export default {
  name: 'App',
  components: {
    MyNetflix
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
