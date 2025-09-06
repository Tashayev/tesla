<template>
  <div class="bg-white p-4 rounded-2xl shadow-md h-full space-y-5 min-h-[150.02px] min-w-42.5 max-w-46">
    <h3 class="text-sm text-gray-500">{{ title }}</h3>
    <p class="text-lg font-bold">{{ infoOne }}
      <span class=" text-base text-gray-500">{{ infoTwo }}</span>
    </p>
    
      <div v-if="showGrafic" ref="chartRef" class="min-w-[137.3px] w-fit h-[30.06px] justify-self-end  "></div>
   </div>
</template>
<script setup>
import { ref, onMounted, nextTick } from 'vue';
import * as echarts from 'echarts';
const props = defineProps({
  title: String,
  infoOne: String,
  infoTwo: String,
  graficData: Array,
  showGrafic: Boolean
});
function colorIndicator(array = []) {
  let sum = array.reduce((acc, num) => acc + num, 0);
  return sum / array.length < 105 ? '#FF0000' : '#008000';
}

const chartRef = ref(null);
onMounted(async () => {
  await nextTick();
  if (chartRef.value && props.showGrafic) {
    const myChart = echarts.init(chartRef.value);
    const option = {
      xAxis: { show: false, type: "category", boundaryGap: false },
      yAxis: { show: false, type: "value" },
      series: [
        {
          type: "line",
          smooth: 0.6,
          symbol: "none",
          lineStyle: { color: colorIndicator(props.graficData), width: 2 },
          areaStyle: {
            color: {
              type: "linear",
              x: 0,
              y: 0,
              x2: 0,
              y2: 1,
              colorStops: [
                { offset: 0, color: colorIndicator(props.graficData) === '#FF0000' ? "rgba(255, 0, 180, 0.33)" : 'rgba(0, 255, 180, 0.33)' },
                { offset: 1, color: colorIndicator(props.graficData) === '#FF0000' ? "rgba(255, 245, 247, 1)" : "rgba(224, 255, 230,1)" }
              ]
            }
          },
          data: props.graficData
        }
      ]
    };
    myChart.setOption(option);
  }
});

</script>