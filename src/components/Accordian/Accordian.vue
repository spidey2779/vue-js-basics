<script setup>
import { ref } from 'vue'

const Accordian = ref([
  {
    title: 'Ichigo Kurosaki',
    content:
      'Ichigo Kurosaki is the main protagonist of the Bleach series. He is a Substitute Shinigami who becomes a Shinigami after meeting Rukia Kuchiki. He possesses immense spiritual power and has the ability to see ghosts.',
    open: false
  },
  {
    title: 'Kenpachi Zaraki',
    content:
      'Kenpachi Zaraki is the captain of the 11th Division, known for his love of battle and immense physical strength. He seeks out strong opponents to fight and has a wild and fearsome reputation.',
    open: false
  },
  {
    title: 'Kisuke Urahara',
    content:
      'Kisuke Urahara is a former captain of the 12th Division and founder of the Urahara Shop. He is a genius inventor and scientist, known for his laid-back personality and mysterious past.',
    open: false
  }
])
const open=(index)=>{
    Accordian.value[index].open= !Accordian.value[index].open
}
</script>
<template>
  <div class="h-screen p-1 bg-zinc-700">
    <div v-for="(item,index) in Accordian" :key="index" class="bg-white w-[40rem] mx-auto my-3 ">
        <div class="flex items-center justify-between p-2 font-mono font-bold cursor-pointer bg-lime-50"  @click="open(index)">{{ item.title }} <span >{{ item.open ? '🔽'  : '▶️'}}</span></div>
        <div v-show="item.open" class="p-4 font-semibold text-white bg-lime-700">
            {{ item.content }}
        </div>
    </div>
  </div>
</template>
//
