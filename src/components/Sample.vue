<script setup>
import { ref ,computed } from 'vue';

 let val=ref('2')
    const squaredVal=computed(()=> val.value **2)
</script>

<template>
    <div class="">
        <div>{{ val }}</div>
        <div>normal way val{{ val**2 }}</div>
        <div>the squared {{ squaredVal }}</div>
        <button @click="val++">increment</button>
        
    </div>
</template>