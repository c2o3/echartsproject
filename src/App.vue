<template>
  <router-view/>
</template>
<script setup>
  import { provide } from 'vue';
  import * as echarts from 'echarts';
  import axios from 'axios';
  provide('echarts', echarts);
  provide('axios', axios);

  axios.defaults.baseURL = 'http://localhost:8888';
</script>
<style lang="scss">
body{
  height: 100vh;
  background-image: url('../src/assets/bg.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
