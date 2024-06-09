<script setup>
import { computed, ref } from 'vue'

let details = ref({
  username: '',
  password: '',
  email: ''
})
let nameValid = computed(() => details.value.username.trim().length > 0)
let emailValid = computed(() => details.value.email.trim().includes('@'))
let passwordValid = computed(() => details.value.password.length > 8)
let formValid = computed(() => nameValid.value && emailValid.value && passwordValid.value)
const submitHandler = () => {
  console.log(nameValid.value, emailValid.value, passwordValid.value)
  console.log(formValid.value)
  if (formValid.value) {
    alert('form submitted successfully')
  } else {
    alert('invalid details')
  }
}
</script>
<template>
  <form
    class="flex flex-col justify-between gap-3 items-center p-3 bg-zinc-50 w-[20rem] h-fit mx-auto my-5"
    @submit.prevent="submitHandler"
  >
    <div class="w-full">
      <input
        type="text"
        placeholder="Username"
        class="w-full p-2 font-semibold text-black border border-black border-solid rounded-sm shadow-sm bg-slate-200"
        v-model="details.username"
      />
      <span class="text-red-500" v-show="!nameValid">Please Enter valid username</span>
    </div>
    <div class="w-full">
      <input
        type="email"
        placeholder="Email"
        v-model="details.email"
        class="w-full p-2 font-semibold text-black border border-black border-solid rounded-sm shadow-sm bg-slate-200"
      />
      <span class="text-red-500" v-show="!emailValid">Please Enter valid Email</span>
    </div>
    <div class="w-full">
      <input
        type="password"
        placeholder="Password"
        v-model="details.password"
        class="w-full p-2 font-semibold text-black border border-black border-solid rounded-sm shadow-sm bg-slate-200"
      />
      <span class="text-red-500" v-show="!passwordValid"
        >Password should be greater than 8 characters</span
      >
    </div>
    <button
      type="submit"
      class="px-8 py-2 text-white transition-colors duration-500 rounded bg-sky-400 hover:bg-sky-500"
    >
      Submit
    </button>
  </form>
</template>
