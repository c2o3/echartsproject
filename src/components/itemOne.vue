<template>
  <div class="">
    <h2>销售总表</h2>
    <div class="chart" id="chartOne"></div>
  </div>
</template>

<script setup>
import { inject, onMounted, reactive } from "vue";
let $echarts = inject("echarts");
let $http = inject("axios");
let data = reactive({});
let xData = reactive([]);
let yData = reactive([]);
function setData() {
  xData = data.data.chartOne.chartData.map((v) => v.title);
  yData = data.data.chartOne.chartData.map((v) => v.num);
}
async function getState() {
  data = await $http({ url: "/one/data" });
}
onMounted(() => {
  let myChart = $echarts.init(document.getElementById("chartOne"));
  getState().then(() => {
    setData();
    myChart.setOption({
      grid: {
        top: "3%",
        right: "2%",
        left: "3%",
        bottom: "3%",
        containLabel: true
      },
      xAxis: {
        type: "value",
      },
      yAxis: {
        type: "category",
        data: xData,
      },
      series: [
        {
          data: yData,
          type: "bar",
          itemStyle: {
            normal: {
              barBorderRadius: [0, 20, 20, 0],
              color: new $echarts.graphic.LinearGradient(0, 0, 1, 0, [
                {
                  offset: 0,
                  color: "#00bcd4",
                },
                {
                  offset: 0.5,
                  color: "#00bcd4",
                },
                {
                  offset: 1,
                  color: "#00bcd4",
                },
              ]),
            },
          },
        },
      ],
    });
  });
});
</script>

<style scoped lang="scss">
h2 {
  height: 0.6rem;
  color: #fff;
  line-height: 0.6rem;
  font-size: 0.25rem;
  text-align: center;
}
.chart {
  width: 100%;
  height: 4.5rem;
}
</style>
