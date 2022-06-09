<template>
  <div class="Player">
    <p>Logged in</p>
    <p>The variable is {{loggedIn}}</p>
  </div>
</template>

<script>
export default {
  name: 'PlayerView'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.Player{
    width:100%;
    height:100%;
}
</style>
