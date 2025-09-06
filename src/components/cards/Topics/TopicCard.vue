<script setup>
const props = defineProps({
  title: String,
  topics: Array,
  index: Number
})
</script>

<template>
  <div class="w-full h-[300px] bg-white rounded-3xl flex flex-col p-7 space-y-5 shadow-md">
    <p class="text-gray-600">{{ title }}</p>
    <div class="flex w-full gap-3" v-for="topic in topics">
      <img :src="topic.image" alt="" class="w-12 h-10 mb-2" />
      <div class="flex flex-col w-full">
        <p class="text-start text-sm font-bold">{{ topic.title }}</p>
        <div class="flex items-center gap-3">
          <div class="relative w-full h-2 bg-green-100 rounded-lg">
            <div :style="{ width: `${topic.percentage}%` }"
              :class="['absolute top-0 left-0 h-2 rounded-lg bg-gradient-to-r', index === 0 ? 'from-[#FF4080] to-[#FFBF1A]' : 'from-[#2FEA9B] to-[#7FDD53]']"></div>
          </div>
          <span class="text-sm font-medium">{{ topic.percentage }}%</span>
          <span class="text-gray-400 text-sm">correct</span>
        </div>
      </div>
    </div>
  </div>
</template>
