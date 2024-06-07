<script setup>
const vFormat = {
  mounted: (element, binding) => {
    element.style.color = binding.value
    console.log(binding.value)
  }
}
const vFont = (element) => {
   element.style.fontSize = '2rem'
}
</script>
<template>
  <div v-format="'red'">this is my div</div>
  <div v-font>this is font div</div>
</template>
