<template>
    <div>
      <h1>Signup</h1>
      <form @submit.prevent="signUp">
        ID : <input type="text" v-model.trim="username">
        <br>
        Password : <input type="password" v-model.trim="password1">
        <br>
        password 확인:<input type="password" v-model.trim="password2">
        <br>
        1년 내 여행횟수 : <input type="text" v-model.trim="travel">
        <input type="submit" value="가입">
      </form>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import { useCounterStore } from '@/stores/counter'
  
  const store = useCounterStore()
  const username = ref(null)
  const password1 = ref(null)
  const password2 = ref(null)
  const travel = ref(null)
  
  const signUp = function () {
    const payload = {
      username: username.value,
      password1: password1.value,
      password2: password2.value,
      travel: travel.value,
    }
    store.signUp(payload)
  }
  
  
  </script>
  
  <style>
  
  </style>
  