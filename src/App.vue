<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';
import Sidebar from './components/sidebar/Sidebar.vue';
import Home from './pages/Home.vue';

const isSidebar = ref(true);

function handleResize() {
  if (window.innerWidth < 640) {
    isSidebar.value = false;
  } else {
    isSidebar.value = true;
  }
}

function toggleSidebar() {
  isSidebar.value = !isSidebar.value;
}

onMounted(() => {
  handleResize();
  window.addEventListener('resize', handleResize);
});

onBeforeUnmount(() => {
  window.removeEventListener('resize', handleResize);
});
</script>

<template>
  <div class="flex max-w-360 mx-auto">
    <Sidebar v-if="isSidebar"/>
    <Home :toggleSidebar="toggleSidebar" :isSidebar="isSidebar"/>
  </div>
</template>
