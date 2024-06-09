<script setup>
import { ref } from 'vue'

const steps = ref(['Step 1', 'Step 2', 'Step 3', 'Step 4', 'Step 5'])
let currentStep = ref(0)

const nextStep = () => {
  if (currentStep.value < steps.value.length - 1) {
    currentStep.value++
  }
}
const prevStep = () => {
  if (currentStep.value > 0) {
    currentStep.value--
  }
}
</script>
<template>
  <div>
    <div class="grid items-center justify-center grid-cols-5 mx-auto my-4 w-fit">
      <div
        v-for="(step, index) in steps"
        :key="index"
        class="rounded-md bg-slate-300 w-[6rem] p-3"
        :class="{ 'bg-green-400': index === currentStep }"
      >
        {{ step }}
      </div>
    </div>
    <div class="flex items-center justify-between gap-5 mx-auto my-4 w-fit">
      <button
        @click="prevStep"
        class="px-4 py-2 rounded-md bg-fuchsia-600 w-[8rem] text-white font-semibold disabled:opacity-30"
        :disabled="currentStep === 0"
      >
        Previous
      </button>
      <button
        @click="nextStep"
        class="px-4 py-2 bg-orange-500 rounded-md w-[8rem] text-white font-semibold disabled:opacity-30"
        :disabled="currentStep === steps.length - 1"
      >
        Next
      </button>
    </div>
  </div>
</template>


