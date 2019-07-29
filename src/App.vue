<template>
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">id: </label>
      <input type="text" id="username" v-model="username">
    </div>
    <div>
      <label for="password">password: </label>
      <input type="text" id="password" v-model="password">
    </div>
    <button type="submit">login</button>
  </form>
</template>

<script>

  import * as axios from "axios";

  export default {
    name: 'app',
    data: function () {
      return {
        username: '',
        password: '',
      }
    },
    methods: {
      submitForm: function () {
        console.log((this.username + " " + this.password));
        var url = 'https://jsonplaceholder.typicode.com/users';
        var data = {
          username: this.username,
          password: this.password
        };
        axios.post(url, data).then(
          function (res) {
            console.log(res);

          }
        ).catch(function (err) {
          console.log(err);
        });
      }
    }
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
