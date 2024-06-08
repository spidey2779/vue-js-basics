<script setup>
import { ref ,computed } from 'vue'

const buttons = ref([
  '7',
  '8',
  '9',
  '/',
  '4',
  '5',
  '6',
  '*',
  '1',
  '2',
  '3',
  '-',
  '.',
  '0',
  '=',
  '+'
])
const inputValue=ref('0')
const addToInput=(text)=>{
    if(inputValue.value==='0'){
        inputValue.value=text
    }
    else{
        inputValue.value+=text
        
    }
}
const getAnswer=()=>{
    try{
        inputValue.value=eval(inputValue.value)
    }
    catch(e) {
        inputValue.value="syntax error";
        setTimeout(() => {
            inputValue.value='0'
        }, 300);
    }
}
const clearDisplay=()=>{
    inputValue.value='0'
}
</script>
<template>
  <div class="h-auto mx-auto my-4 shadow-xl drop-shadow-md bg-zinc-50 w-fit">
    <div>
      <input type="text" v-model="inputValue" class="w-full p-2 font-semibold border-2 border-black bg-sky-100"
    </div>
    <div class="grid w-[15rem] grid-rows-5 grid-cols-4 gap-2" >
      <button @click="button ==='=' ? getAnswer() : addToInput(button)" v-for="button in buttons" class="h-[2rem] bg-white shadow" :class="button==='=' ? 'bg-green-400' : ''">{{ button }}</button>
      <button class="col-span-4 text-white bg-red-600 rounded-sm" @click="clearDisplay">clear</button>
    </div>
  </div>
</template>
