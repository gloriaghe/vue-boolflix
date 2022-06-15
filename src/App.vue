<template>
  <div id="app">
    <MyHeader/>
    <MyNetflix/>
  </div>
</template>

<script>
import MyNetflix from './components/MyNetflix.vue'
import MyHeader from './components/MyHeader.vue'


export default {
  name: 'App',
  components: {
    MyNetflix,
    MyHeader
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


<!-- <template>
  <div id="app">
    <MyHeader/>
    <MyNetflix/>
  </div>
</template>

<script>
import MyNetflix from './components/MyNetflix.vue'
import MyHeader from './components/MyHeader.vue'


export default {
  name: 'App',
  components: {
    MyNetflix,
    MyHeader
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
