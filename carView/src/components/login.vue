<template>
  <div id='loginScreen'>
      <input type="button" value="Login" v-on:click="onLogin">
    <div>
      <div id='login'>
        <h1>First, log in to spotify</h1>
        <a href='/login'>Log in</a>
      </div>
      <div id='loggedin'>

      </div>
    </div>

    <script id="loggedin-template" type="text/x-handlebars-template">
      <h1>Logged in as </h1>
      <img id="avatar" width="200" src="" />
      <dl>
        <dt>Display name</dt><dd></dd>
        <dt>Username</dt><dd></dd>
        <dt>Email</dt><dd></dd>
        <dt>Spotify URI</dt><dd><a href=""></a></dd>
        <dt>Link</dt><dd><a href=""></a></dd>
        <dt>Profile Image</dt><dd></dd>
      </dl>
      <p><a href="/">Log in again</a></p>
    </script>
  </div>
</template>

<script>
import Vue from "vue";
import $ from 'jquery'
import queryString from 'query-string'



var request = require('request')
var authorized = false;
var authenticated = false;
var client_id = '2dd6a5ff92b54ac58c3f1b901786e464' // Your client id
var client_secret = 'c07fba882d88428993138a98a3034cd8' // Your secret
var redirect_uri = 'http://localhost:8080/#/' // Your redirect uri
var scopes = 'user-read-private user-read-email'

var authOptions = {
  url: 'https://accounts.spotify.com/api/token',
  headers: {
    'Authorization': 'Basic ' + (new Buffer(client_id + ':' + client_secret).toString('base64'))
  },
  form: {
    grant_type: 'client_credentials'
  },
  json: true
};

//Getting the authorization endpoint

// var express = require('express')
// var app = express()

// function onLogin(oEvent){
//     app.get('/login', function(req, res) {

//     var state = generateRandomString(16);
//     var scope = 'user-read-private user-read-email streaming user-read-playback-state';

//     res.redirect('https://accounts.spotify.com/authorize?' +
//         querystring.stringify({
//         response_type: 'code',
//         client_id: client_id,
//         scope: scope,
//         redirect_uri: redirect_uri,
//         state: state
//         }));
//     });
// }




request.post(authOptions, function( error, response, body) {
  if (!error && response.statusCode === 200) {
      authorized = true

    // use the access token to access the Spotify Web API
    console.log(body)
    var token = body.access_token
    var options = {
      url: 'https://api.spotify.com/v1/users/11135484247',
      headers: {
        'Authorization': 'Bearer ' + token
      },
      json: true
    };
    request.get(options, function(error, response, body) {
      console.log(body)
    });
  }
});

export default {
  data() {
    return {
      message: 'Hello World!'
    }
  },
  methods: {
    onLogin(oEvent) {
        console.log(oEvent);
        var state = this.makeid(16);
        var scope = 'user-read-private user-read-email streaming user-read-playback-state';
        $.ajax({
            type: "GET",
            url: 'https://accounts.spotify.com/authorize?' + queryString.stringify({
                response_type: 'code',
                client_id: client_id,
                scope: scope,
                redirect_uri: redirect_uri,
                state: state
            }),
            headers: {'Access-Control-Allow-Headers': 'X-Requested-With'}
        },(res) =>{
            console.log(res);
        });
        //this.message = this.message.split('').reverse().join('')
    },
    makeid(length) {
        var result           = '';
        var characters       = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
        var charactersLength = characters.length;
        for ( var i = 0; i < length; i++ ) {
        result += characters.charAt(Math.floor(Math.random() * 
    charactersLength));
    }
    return result;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#login {
  display: none;
}

#loggedin {
  display: none;
}
</style>