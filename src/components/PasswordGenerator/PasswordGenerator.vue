<script setup>
import { ref } from 'vue'
let passLength = ref('8')
let includeUppercase = ref(false)
let includeSymbols = ref(false)
let includeDigits = ref(false)
let generatedPassword = ref('')
const generateThePassword = () => {
  generatedPassword.value = ''
  let Uppercase = includeUppercase.value ? 'ABCDEFGHIJKLMNOPQRSTUVWXYZabc' : ''
  let lowercase = 'abcdefghijklmnopqrstuvwxyz'
  let symbols = includeSymbols.value ? "!@#$%^&*()*+<=>,.?/|'" : ''
  let digits = includeDigits.value ? '0123456789' : ''
  let Passwordcontainer = lowercase + Uppercase + symbols + digits
  let pass = ''
  for (let i = 0; i < passLength.value; i++) {
    let randomIndex = Math.floor(Math.random() * Passwordcontainer.length)
    pass += Passwordcontainer[randomIndex]
  }
  generatedPassword.value = pass
}
</script>
<template>
  <h1 class="font-mono text-4xl font-bold text-center" >Password Generator Using Vue js</h1>
  <div
    class="flex flex-col w-[20rem] bg-zinc-700 text-white rounded-md my-5 mx-auto p-4 items-start gap-3"
  >
    <div class="w-full">
      <label for="len">Enter Password length :</label>
      <input
        type="number"
        class="w-full p-2 text-black border-2 rounded border-lime-100"
        id="len"
        min="8"
        max="32"
        v-model="passLength"
      />
    </div>
    <div class="flex items-center justify-between gap-4 p-1 ">
      <label for="upper">Include Uppercase :</label>
      <input type="checkbox" class="border-2 border-black" id="upper" v-model="includeUppercase" />
    </div>
    <div class="flex items-center justify-between gap-4 p-1 ">
      <label for="symbols">Include Symbols :</label>
      <input type="checkbox" class="border-2 border-black" id="symbols" v-model="includeSymbols" />
    </div>
    <div class="flex items-center justify-between gap-4 p-1 ">
      <label for="digits">Include Digits :</label>
      <input type="checkbox" class="border-2 border-black" id="digits" v-model="includeDigits" />
    </div>
    <div>
      Generated Password :
      <input
        type="text"
        readonly
        class="w-full p-2 text-black rounded"
        v-model="generatedPassword"
      />
    </div>
    <button
      class="self-center px-5 py-2 text-black rounded shadow-md bg-pink-50"
      @click="generateThePassword"
    >
      Generate Password
    </button>
  </div>
</template>
