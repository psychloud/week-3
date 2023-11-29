<script setup lang="ts">
import { ref } from 'vue';
import axios from 'axios';
import { useAuthStore } from '@/stores/auth';
import { useRouter } from 'vue-router';
const auth = useAuthStore()
const router = useRouter()

const username = ref('')
const password = ref('')

const onLogin = async () => {
  if(username.value === "" || password.value === "") {
    alert("Username or Password can't be empty")
  } else {
  try {
    const response = await axios.post('http://localhost:3000/login', {
      username: username.value,
      password: password.value,
    })
    
    auth.login(username.value, password.value)
    console.log(response);
  } catch (error) {
    console.error('Login error:', error);
  }
}
}
console.log(Response)
</script>

<style>
.inputButton{
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.input {
  margin-bottom: 10px;
  border-radius: 0.25rem;
  border-style:groove;
  padding-top: 0.2rem;
  padding-bottom: 0.2rem;
}

.button {
  color: white;
  background-color: blue;
  border-radius: 0.25rem;
  font-size: 2rem;
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
  transition-timing-function: ease-in-out;
  transition-duration: 0.25s;
}

.button:hover {
  color: blue;
  background-color: white;
  transition-timing-function: ease-in-out;
  transition-duration: 0.25s;
}


</style>

<template>
  <div>
    <h1>Login Page</h1>
    <div class="inputButton">
      <input class="input" type="text" v-model="username" placeholder="username">
      <input class="input" type="password" v-model="password" placeholder="password">
      <button class="button" @click="onLogin()">Login</button>
    </div>
  </div>
</template>