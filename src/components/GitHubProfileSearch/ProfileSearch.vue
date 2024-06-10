<script setup>
import axios from 'axios'
import { ref } from 'vue'
const username = ref('')
const userData = ref(null)
const loading = ref(false)
const myerror = ref(null)
const fetchData = async () => {
  if (username.value.trim().length === 0) {
    alert('Enter username')
    return
  }
  loading.value = true
  userData.value = null
  myerror.value = null
  try {
    loading.value = true
    const response = await axios.get(`https://api.github.com/users/${username.value}`)
    userData.value = response.data
    // console.log(response.data)
  } catch (error) {
    myerror.value = error.response?.data?.message || 'Error fetching data'
    // console.log('error fetching data', error)
    
  } finally {
    loading.value = false
  }
}
</script>
<template>
  <main class="bg-zinc-800 h-full min-h-screen text-white">
    <h1 class="text-[2rem] font-semibold text-center p-2">Git Hub Profile Viewer</h1>
    <div class="p-2 flex justify-center items-center gap-5">
      <input
        type="text"
        v-model="username"
        placeholder="Enter Github Profile Name"
        class="w-[15rem] p-2 b text-black font-semibold outline-none border-zinc-300 border-2 rounded-md"
        @keypress.enter="fetchData"
      />
      <button
        @click="fetchData"
        class="bg-sky-600 text-white py-2 px-3 rounded-md disabled:opacity-30"
        :disabled="loading"
      >
        Search Profile
      </button>
    </div>
    <div v-if="myerror" class="text-center text-red-500">{{ myerror }}. Search Again</div>
    <div
      class="w-[30rem] bg-zinc-500 flex flex-col mx-auto gap-4 p-4 shadow-md rounded-lg text-white text-[1.2rem] capitalize font-semibold"
      v-if="userData && !loading"
    >
      <div class="overflow-hidden p-2 grid place-content-center">
        <img
          :src="userData.avatar_url"
          alt="Profile Image"
          class="h-[15rem] w-[15rem] rounded-full p-2 bg-black object-cover object-center"
        />
      </div>
      <div><strong>Name :</strong> {{ userData.name || username }}</div>
      <div><strong>Location :</strong> {{ userData.location || 'location not defined'}}</div>
      <div><strong>Public repos :</strong> {{ userData.public_repos }}</div>
      <div><strong>Bio :</strong> {{ userData.bio || 'Nothing in Bio' }}</div>
    </div>
    <div v-else-if="loading" class="text-center p-5">Loading...</div>
    <div v-else-if="!loading && !myerror && !userData" class="text-center p-5">Enter something to search </div>
  </main>
</template>
