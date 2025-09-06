<template>
  <div class="md:flex block space-y-3 justify-between gap-5 w-full ">
    <div class="relative w-full  ">
      <div @click="toggle('timeframe')" class="px-4 py-2 bg-white rounded-xl shadow-md w-full text-left flex justify-between cursor-pointer
       items-center">
        <div>
          Timeframe: <span class="font-bold">{{ selected.timeframe }}</span>
        </div>
        <div>
          <svg width="8" height="6" viewBox="0 0 8 6" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path
              d="M0.472614 2.41374L3.03053 5.00374C3.41569 5.39373 4.03789 5.39373 4.42306 5.00374L6.98097 2.41374C7.60316 1.78374 7.15874 0.703735 6.27976 0.703735H1.16394C0.284968 0.703735 -0.149581 1.78374 0.472614 2.41374Z"
              fill="black" />
          </svg>

        </div>
      </div>
      <ul v-if="openMenu === 'timeframe'" class="absolute mt-1 w-full bg-white rounded-xl shadow z-30">
        <li v-for="option in timeOptions" :key="option" class="px-4 py-2 hover:bg-gray-200 cursor-pointer "
          @click="select('timeframe', option)">
          {{ option }}
        </li>
      </ul>
    </div>
    <div class="relative w-full ">
      <div @click="toggle('people')" class="px-4 py-2 bg-white rounded-xl shadow-md w-full text-left flex justify-between items-center cursor-pointer">
        <div>
          People: <span class="font-bold">{{ selected.people }}</span>
        </div>
        <div>
          <svg width="8" height="6" viewBox="0 0 8 6" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path
              d="M0.472614 2.41374L3.03053 5.00374C3.41569 5.39373 4.03789 5.39373 4.42306 5.00374L6.98097 2.41374C7.60316 1.78374 7.15874 0.703735 6.27976 0.703735H1.16394C0.284968 0.703735 -0.149581 1.78374 0.472614 2.41374Z"
              fill="black" />
          </svg>

        </div>
      </div>
      <ul v-if="openMenu === 'people'" class="absolute mt-1 w-full bg-white  rounded-xl shadow z-30">
        <li v-for="option in peopleOptions" :key="option" class="px-4 py-2 hover:bg-gray-200 cursor-pointer"
          @click="select('people', option)">
          {{ option }}
        </li>
      </ul>
    </div>
    <div class="relative w-full ">
      <div @click="toggle('topic')" class="px-4 py-2 bg-white rounded-xl shadow-md w-full text-left flex justify-between items-center cursor-pointer">
        <div>
          Topic: <span class="font-bold">{{ selected.topic }}</span>
        </div>
        <div>
          <svg width="8" height="6" viewBox="0 0 8 6" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path
              d="M0.472614 2.41374L3.03053 5.00374C3.41569 5.39373 4.03789 5.39373 4.42306 5.00374L6.98097 2.41374C7.60316 1.78374 7.15874 0.703735 6.27976 0.703735H1.16394C0.284968 0.703735 -0.149581 1.78374 0.472614 2.41374Z"
              fill="black" />
          </svg>

        </div>
      </div>
      <ul v-if="openMenu === 'topic'" class="absolute mt-1 w-full bg-white
         rounded-xl shadow z-30">
        <li v-for="option in topicOptions" :key="option" class="px-4 py-2 hover:bg-gray-200 cursor-pointer"
          @click="select('topic', option)">
          {{ option }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { reactive, ref } from "vue";

const timeOptions = ["All Time", "Exact period", "Last 7 days", "Last month"];
const peopleOptions = ["All", "Current person", "Last person"];
const topicOptions = ["All", "Current topic", "Last topic"];

const selected = reactive({
  timeframe: timeOptions[0],
  people: peopleOptions[0],
  topic: topicOptions[0],
});

const openMenu = ref(null);

function toggle(menu) {
  openMenu.value = openMenu.value === menu ? null : menu;
}

function select(menu, option) {
  selected[menu] = option;
  openMenu.value = null;
}
</script>
