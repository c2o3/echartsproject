<template>
  <div>
    <h2>周销图</h2>
    <div class="chart" id="chartTwo"></div>
  </div>
</template>

<script setup>
import { inject, onMounted, reactive } from "vue";
let $echarts = inject("echarts");
let $http = inject("axios");
let data = reactive({});

async function getState() {
  data = await $http({ url: "/two/data" });
}
onMounted(() => {
  getState().then(() => {
    let myChart = $echarts.init(document.querySelector("#chartTwo"));
    myChart.setOption({
      tooltip: {
        trigger: 'axis',
        axisPointer: {
          type: 'cross',
          label: {
            backgroundColor: '#6a7985'
          }
        }
      },
      legend:{
        data: ['服饰', '数码', '家电', '家居', '日化']
      },
      grid: {
        left: '1%',
        right: '4%',
        bottom: '3%',
        containLabel: true
      },
      xAxis: {
        type: 'category',
        boundaryGap: false,
        data: data.data.chartTwo.chartData.day,
        axisLine: {
          lineStyle: {
            color: '#fff'
          }
        }
      },
      yAxis: {
        type: 'value',
        axisLine: {
          lineStyle: {
            color: '#fff'
          }
        }
      },
      series:[
        {
          name: '服饰',
          type: 'line',
          data: data.data.chartTwo.chartData.num.Chemicals,
          smooth: true,
          showSymbol: false,
          stack: 'Total',
          lineStyle: {width: 0},
          emphasis: {focus: 'series'},
          areaStyle: {
            opacity: 0.8,
            color: new $echarts.graphic.LinearGradient(
              0, 0, 0, 1,
              [
                { offset: 0, color: 'rgb(128, 255, 165)' },
                { offset: 1, color: 'rgb(1, 191, 236)' }
              ]
            )
          }
        },
        {
          name: '数码',
          type: 'line',
          data: data.data.chartTwo.chartData.num.Clothes,
          smooth: true,
          showSymbol: false,
          stack: 'Total',
          lineStyle: {width: 0},
          emphasis: {focus: 'series'},
          areaStyle: {
            opacity: 0.8,
            color: new $echarts.graphic.LinearGradient(
              0, 0, 0, 1,
              [
                { offset: 0, color: 'rgb(128, 255, 165)' },
                { offset: 1, color: 'rgb(1, 191, 236)' }
              ]
            )
          }
        },
        {
          name: '家电',
          type: 'line',
          data: data.data.chartTwo.chartData.num.Electrical,
          smooth: true,
          showSymbol: false,
          stack: 'Total',
          lineStyle: {width: 0},
          emphasis: {focus: 'series'},
          areaStyle: {
            opacity: 0.8,
            color: new $echarts.graphic.LinearGradient(
              0, 0, 0, 1,
              [
                { offset: 0, color: 'rgb(128, 255, 165)' },
                { offset: 1, color: 'rgb(1, 191, 236)' }
              ]
            )
          }
        },
        {
          name: '家居',
          type: 'line',
          data: data.data.chartTwo.chartData.num.digit,
          smooth: true,
          showSymbol: false,
          stack: 'Total',
          lineStyle: {width: 0},
          emphasis: {focus: 'series'},
          areaStyle: {
            opacity: 0.8,
            color: new $echarts.graphic.LinearGradient(
              0, 0, 0, 1,
              [
                { offset: 0, color: 'rgb(128, 255, 165)' },
                { offset: 1, color: 'rgb(1, 191, 236)' }
              ]
            )
          }
        },
        {
          name: '日化',
          type: 'line',
          data: data.data.chartTwo.chartData.num.gear,
          smooth: true,
          showSymbol: false,
          stack: 'Total',
          lineStyle: {width: 0},
          emphasis: {focus: 'series'},
          areaStyle: {
            opacity: 0.8,
            color: new $echarts.graphic.LinearGradient(
              0, 0, 0, 1,
              [
                { offset: 0, color: 'rgb(128, 255, 165)' },
                { offset: 1, color: 'rgb(1, 191, 236)' }
              ]
            )
          }
        }
      ]
    });
  });
});
</script>

<style scoped lang="scss">
.chart {
  height: 4.5rem;
}
h2 {
  height: 0.6rem;
  color: #fff;
  line-height: 0.6rem;
  font-size: 0.25rem;
  text-align: center;
}
</style>
