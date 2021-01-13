<template>
<!-- .prevent : 새로고침 막기 -->
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">id: </label>
      <input type="text" id="username" v-model="username">
    </div>

    <div>
      <label for="password">pw: </label>
      <input type="password" id="password" v-model="password">
    </div>
    <button type="submit">login</button>
  </form>  
</template>

<script>
import axios from 'axios';

export default {
  data: function(){
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    submitForm: function(){
      // event.preventDefault();   // 페이지 새로고침을 위함
      console.log(this.username, this.password);
      let url = 'https://jsonplaceholder.typicode.com/users';
      let data = {
        username: this.username,
        password: this.password
      }
      axios.post(url, data)
      .then(function(response){
        console.log('response',response);
      })
      .catch(function(error){
        console.log('error',error);
      });
    }
  }
}
</script>

<style>

</style>