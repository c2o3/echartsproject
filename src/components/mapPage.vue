<template>
  <div class="map"></div>
</template>

<script setup>
import { onMounted, reactive, inject } from "vue";
let mapData = reactive({});
let $echarts = inject("echarts");
let $http = inject("axios");
async function getState() {
  mapData = await $http({url: 'map/data'});
  console.log(mapData);
  
}
onMounted(() => {
  getState().then(() => {
    $echarts.registerMap("china", mapData.data.chartMap);
    let myChart = $echarts.init(document.querySelector(".map"));
    myChart.setOption({
      geo: {
        map: "china",
        itemStyle: {
          areaColor: "#0099ff",
          borderColor: "#00ffff",
          shadowColor: "rgba(230, 130, 70, 0.5)",
          shadowBlur: 30,
          emphasis: { focus },
        },
      },
      tooltip: {
        trriger: "item",
      },
      title: {
        text: '城市销量',
        left: '45%',
        textStyle: {
          color: '#fff',
          fontSize: 20,
          textShadowBlur: 10,
          textShadowColor: '#33ffff'
        }
      },
      visualMap: {
        type: "continuous",
        min: 100,
        max: 10000,
        calculate: true,
        inRange: {
          color: ["#50a3ba", "#eac736", "#d94e5d"],
        },
        TextStyle: {
          color: "#fff",
        },
      },
      series: [
        {
          type: "scatter",
          itemStyle: {
            color: "red",
          },
          coordinateSystem: "geo",
          data: [
            { name: "北京", value: [116.46, 39.92, 4367] },
            { name: "上海", value: [121.48, 31.22, 8675] },
            { name: "深圳", value: [114.07, 22.62, 2461] },
            { name: "广州", value: [113.23, 23.16, 187] },
            { name: "西安", value: [108.45, 34, 3421] },
          ],
        },
      ],
    });
  });
});
</script>

<style scoped lang="scss">
.map {
  width: 100%;
  height: 100%;
}
</style>
