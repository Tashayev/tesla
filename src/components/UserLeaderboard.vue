<template>
 <div class="w-full h-fit bg-white p-7 rounded-3xl shadow-md" >
  <p class="text-gray-600 font-bold mb-10">User Leaderboard</p>
  <div v-for="(user, index) in users" :key="index">
    <div class=" flex justify-between">
      <div class="flex items-center w-full gap-5 space-y-5">
        <img :src="user.avatar" alt="ava" width="50" height="50" class="rounded-full">
        <div>
          <p class="font-bold">{{ user.name }}</p>
          <p class="text-gray-500">{{ user.info }}</p>
        </div>
      </div>
      <div class="flex gap-3 items-center">
        <p class="font-bold">{{ index + 1 }}</p>
        <img :src="user.rating" alt="rate" class="w-3 h-3">
      </div>
    </div>
  </div>
 </div>
</template>
<script setup>
import user1 from '../assets/person-1.png'
import user2 from '../assets/person-2.png'
import user3 from '../assets/person-3.png'
import user4 from '../assets/person-4.png'
import up from '../assets/Up.png'
import down from '../assets/Down.png'




const users = [
  {
    name: 'Jesse Thomas',
    info: '637 Points - 98% Correct',
    avatar: user1,
    rating: up
  },
  {
    name: 'Thisal Mathiyazhagan',
    info: '637 Points - 89% Correct',
    avatar: user2,
    rating: down
  },
  {
    name: 'Helen Chuang',
    info: '637 Points - 88% Correct',
    avatar: user3,
    rating: up
  },
  {
    name: 'Lura Silverman',
    info: '637 Points',
    avatar: user4,
    rating: up
  },
]
</script>