<template>
  <div v-if="loggedIn">
    <Player/>
  </div>
  <div v-else>
    <Login/>
  </div>
</template>

<script>
import Player from './components/Player.vue'
import Login from './components/Login.vue'

export default {
  data(){
    return{
      loggedIn: false,
    }
  },
  methods:{
    getStuff(){

    }
  },
  name: 'App',
  components: {
    Player,
    Login
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body{
  margin: 0 0 0 0;
  width:100%;
  height:100%;
}
</style>
