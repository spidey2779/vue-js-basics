<script setup>
import axios from 'axios'
import { ref } from 'vue'
const joke = ref('')
const loading = ref(false)
const fetchJoke = async () => {
  try {
    loading.value = true
    const response = await axios.get('https://icanhazdadjoke.com/', {
      headers: {
        Accept: 'application/json'
      }
    })
    joke.value = response.data.joke
    loading.value = false
  } catch (e) {
    console.log('Error fetching data: ' + e)
    loading.value = false
  }
}
</script>
<template>
  <h1 class="text-center text-2xl font-semibold">Dad Jokes</h1>
  <div class="mx-auto bg-lime-100 w-[30rem] p-3 flex flex-col gap-3">
    <button @click="fetchJoke" class="bg-green-500 rodned-md text-white p-2 w-fit">Get Joke</button>
    <span v-if="loading">loading...</span>
    <span v-if="!joke && !loading">click above to get the jokes </span>
    <div v-show="joke && !loading" class="bg-sky-600 rounded-s-lg p-3 text-white">{{ joke }}</div>
  </div>
</template>
