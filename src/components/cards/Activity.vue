<template>
  <div class="w-full h-[322px] bg-white rounded-2xl shadow p-5">
    <div class="flex justify-between p-1">
      <p>Activity</p>
      <div class="relative">
        <div class="flex gap-2  items-center cursor-pointer" @click="toggleBtn">
          <p>{{ selected }}</p>
          <svg width="10" height="7" viewBox="0 0 10 7" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M1.175 0.816894L5 4.64189L8.825 0.816894L10 2.00023L5 7.00023L5.17251e-08 2.00023L1.175 0.816894Z"
              fill="#848A95" />
          </svg>
        </div>
        <ul v-if="isOpen" class="absolute mt-1 w-25 bg-white z-10 
         rounded-xl shadow">
          <li v-for="option in options" :key="option" @click="select(option)"
            class=" px-4 py-2 hover:bg-gray-200 cursor-pointer  rounded-xl">
            {{ option }}
          </li>
        </ul>
      </div>
    </div>
    <div class="w-full border border-gray-300"></div>
    <div ref="chartRef" class="w-full h-full"></div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount, watch } from "vue";
import * as echarts from "echarts";

const options = ["Days", "Months", "Years"];
const isOpen = ref(false)
const toggleBtn = () => {
  isOpen.value = !isOpen.value
};
const selected = ref(options[0])
function select(option) {
  selected.value = option;
  isOpen.value = false
}


const chartRef = ref(null);
let myChart = null;
const days = ['Sun', 'Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'];
const months = ["JAN", "FEB", "MAR", "APR", "MAY", "JUN", "JUL", "AUG", "SEP", "OCT", "NOV", "DEC"];
const years = ['2020', '2021', '2022', '2023', '2024', '2025'];
const data = [120, 150, 230, 280, 300, 210, 190, 160, 250, 310, 420, 450];
const yMax = 500;
function selectDateForm(form) {
  if (form === "Years") return years;
  if (form === "Months") return months;
  return days;
}

onMounted(() => {
  if (chartRef.value) {
    myChart = echarts.init(chartRef.value);
    updateChart();
    window.addEventListener("resize", () => {
      myChart && myChart.resize();
    });
  }
});

watch(selected, () => {
  updateChart()
});

function updateChart() {
  const option = {
    xAxis: {
      type: "category",
      data: selectDateForm(selected.value),
      axisLabel: { color: "#4B5563" },
      axisTick: { show: false },
      axisLine: { show: false },
    },
    yAxis: {
      splitLine: { show: false },
      axisLine: { show: false },
      axisTick: { show: false },
      axisLabel: { color: "#9CA3AF" },
    },
    grid: {
      left: "5%",
      right: "5%",
      top: "10%",
      bottom: "10%",
      containLabel: true,
    },
    series: [

      {
        type: "bar",
        data: new Array(data.length).fill(yMax),
        barWidth: 10,
        itemStyle: {
          borderRadius: 10,
          color: "#F2F7FF",
        },
        barGap: '-100%',
        silent: true,
        z: 1,
      },

      {
        type: "bar",
        data,
        barWidth: 10,
        itemStyle: {
          borderRadius: 10,
          color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
            { offset: 0, color: "#60A5FA" },
            { offset: 1, color: "#2563EB" },
          ]),
        },
        z: 2,

      },
    ],
    tooltip: {
      trigger: "axis",
    },
  };

  myChart.setOption(option);
}
onBeforeUnmount(() => {
  myChart && myChart.dispose();
});
</script>
