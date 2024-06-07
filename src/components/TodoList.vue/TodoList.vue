<script setup>
import { ref } from 'vue'

const todos = ref([])
const newTodo = ref('')
const addTodo = () => {
  if (newTodo.value.trim() !== '') {
    todos.value.push(newTodo.value)
    newTodo.value = ''
    return
  } else {
    return alert('Please enter a Todo!')
  }
}
const deleteTodo = (myindex) => {
  //   console.log(myindex)
  todos.value.splice(myindex, 1)
}
</script>
<template>
  <div class="bg-zinc-200 h-screen w-full py-1">
    <main class="bg-yellow-50 w-[30rem] mx-auto mt-3 flex flex-col gap-2 shadow-inner shadow-xl">
      <div class="bg-white flex items-center justify-between gap-1 p-2">
        <input
          type="text"
          placeholder="Enter Todo"
          @keypress.enter="addTodo"
          v-model="newTodo"
          class="bg-blue-50 w-full h-full p-3 outline-none shadow"
        />
        <button @click="addTodo" class="bg-green-400 px-6 py-3 rounded-sm font-semibold hover:bg-green-500 transition-all duration-500">
          Add
        </button>
      </div>
      <ul class="flex flex-col gap-2 p-3">
        <li v-show="todos.length === 0" class="text-center font-semibold">No Todos yet.</li>
        <li
          v-for="(todo, index) in todos"
          class="bg-white flex items-center justify-between px-10 font-semibold py-2 shadow-lg"
        >
          {{ todo }}
          <button @click="deleteTodo(index)" class="bg-red-600 p-2 rounded-md hover:bg-red-700 transition-all duration-400">DEL</button>
        </li>
      </ul>
    </main>
  </div>
</template>
