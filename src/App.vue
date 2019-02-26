<template>
  <div id="app">
    <img src="./assets/logo.png">
    <ghz></ghz>
    <router-view/>
  </div>
</template>

<script>
import HE from './ghz.vue'
export default {
  name: 'App',
  components:{
    ghz:HE
  },
  created() {
    alert()
    // console.log(ghz)
  },
  

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
