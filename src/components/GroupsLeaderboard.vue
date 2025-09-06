<template>
 <div class="w-full h-fit bg-white p-7 rounded-3xl shadow-md" >
  <p class="text-gray-600 font-bold mb-10">Groups Leaderboard</p>
  <div v-for="(group, index) in groups" :key="index">
    <div class=" flex justify-between space-y-5">
      <div class="flex items-center w-full gap-5 ">        
        <div>
          <p class="font-bold">{{ group.name }}</p>
          <p class="text-gray-500">{{ group.info }}</p>
        </div>
      </div>
      <div class="flex gap-3 items-center">
        <p class="font-bold">{{ index + 1 }}</p>
        <img :src="group.rating" alt="rate" class="w-3 h-3">
      </div>
    </div>
  </div>
 </div>
</template>
<script setup>
import up from '../assets/Up.png'
import down from '../assets/Down.png'




const groups = [
  {
    name: 'Houston Facility',
    info: '52 Points/User - 97% Correct',    
    rating: up
  },
  {
    name: 'Test Group',
    info: '52 Points/User - 95% Correct',    
    rating: down
  },
  {
    name: 'Sales Leadership',
    info: '52 Points/User - 87% Correct',   
    rating: up
  },
  {
    name: 'Northeast Region',
    info: '52 Points/User',    
    rating: up
  },
]
</script>