<template>
  <div class="grid md:grid-cols-3 grid-cols-2 gap-3 w-full ">
   
    <div v-for="value in cards">
      <OneCard 
        :title="value.title"
        :grafic-data="value.graficData"
        :info-one="value.indicatorOne"
        :info-two="value.indicatorTwo"
        :show-grafic="value.showGraph"
      />
    </div>
    
   </div> 
</template>

<script setup>
import { ref} from "vue";

import OneCard from "./OneCard.vue";
const maxNum = 130;
const minNum = 80;

function randomArrayGenerarator(max, min) {
  const arrayLength = 20;
  const newArray = [];
  for (let i = 0; i < arrayLength; i++) {
    let randomNum = Math.floor(Math.random() * (max - min) + min);
    newArray.push(randomNum);
  }
  return newArray;
}

const cards = ref([
  { title: "Active Users", indicatorOne: "27", indicatorTwo: "/80", showGraph: false },
  { title: "Questions Answered", indicatorOne: "3,289", showGraph: false },
  { title: "Av. Session Lenght", indicatorOne: "2m 34s", showGraph: false },
  { title: "Starting Knowledge", indicatorOne: "64%", showGraph: true, graficData: randomArrayGenerarator(maxNum, minNum) },
  { title: "Current Knowledge", indicatorOne: "86%", showGraph: true, graficData: randomArrayGenerarator(maxNum, minNum) },
  { title: "Knowledge Gain", indicatorOne: "+34%", showGraph: true, graficData: randomArrayGenerarator(maxNum, minNum) },
]);


</script>
