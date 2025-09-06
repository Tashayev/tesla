<template>
  <div class="space-y-5">
      <div class="border-gray-400 border-t w-[190px]  "></div>
      <div>
        <img :src="avatar" alt="ava" width="50" height="50" class="rounded-full">
        <p>Sam Wheeler</p>
        <p class="text-gray-400">samwheeler@gmail.com</p>

      </div>
    </div>
</template>
<script setup>
import avatar from '../../assets/avatar.jpg'
</script>