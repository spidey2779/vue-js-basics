<script setup>
import Sample from './components/Sample.vue'
import SampleTwo from './components/SampleTwo.vue'
import Hello from './components/Hello.vue'
import {ref} from 'vue';
const currentTab = ref('Sample')
const tabs = {
  Sample,
  SampleTwo,
  Hello
}
</script>

<template>
  <h1>this is main component</h1>
  <button @click="currentTab = 'Sample'">first page</button>
  <button @click="currentTab = 'SampleTwo'">second page</button>
  <button @click="currentTab = 'Hello'">third page</button>
  <component :is="tabs[currentTab]"/>
</template>
