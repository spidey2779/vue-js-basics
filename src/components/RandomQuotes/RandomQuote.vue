<script setup>
import { onMounted, reactive, ref } from 'vue'
import { quotes } from './quotes'
const myquotes = reactive(quotes)
const currentQuote = ref({ author: '', quote: '' })
const getRandomQuotes = () => {
  const myindex = Math.floor(Math.random() * myquotes.length)
  currentQuote.value.quote = myquotes[myindex].quote
  currentQuote.value.author = myquotes[myindex].author
}
onMounted(getRandomQuotes)
</script>
<template>
  <div class="w-[40rem] bg-zinc-50 my-20 mx-auto rounded-md p-4 flex flex-col items-center shadow-md ">
    <h1 class="text-center font-bold text-3xl font-mono">Random Quote Generator</h1>
    <div class="bg-white px-10 py-5 flex flex-col gap-3 m-5 h-[10rem] w-full">
      <p class="normal-case h-[70%]">{{ currentQuote.quote }}</p>
      <span class="font-bold text-xl text-center">{{ currentQuote.author }}</span>
    </div>
    <button @click="getRandomQuotes" class="bg-sky-400 text-white p-3 rounded w-fit">
      Generate Quote
    </button>
  </div>
</template>
