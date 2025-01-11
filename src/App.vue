<template>
  <form @submit.prevent="submitForm">
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

<script setup>
import { ref } from 'vue';
import axios from 'axios';

const username = ref('');
const password = ref('');

function submitForm(){
  console.log(username.value, password.value)
  var url = 'https://jsonplaceholder.typicode.com/posts';
  var data = {
    username: username.value,
    password: password.value
  }
  axios.post(url, data)
    .then(response => {
      console.log(response);
    })
    .catch(error => {
      console.error(error);
    });
}
</script>

<style lang="scss" scoped>

</style>