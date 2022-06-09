<template>
    <div class="login">
        <input type="button" value="asd"/>
    </div>
</template>

<script>
export default {
  name: 'LogIn',
  props: {
    msg: String
  },
  data() {
    return {
      auth : {},
    };
  },
  methods:{
    async authenticate(){
      try{
          const response = await this.$http.get(
          'https://api.spotify.com/v1/tracks/2TpxZ7JUBn3uw46aR7qd6V'
        );
        this.auth = response.data;
      }catch (err){
          console.log(err);
      }
    }
  },
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
</style>
