<script>
import fy from 'paging-pdf';
import { onMounted } from 'vue';
import AutoSizeEchart from 'auto-size-echart';

export default {
  name: 'demo',
  props: {
    msg: String,
  },
  setup(props) {
    const options = {
      chart1: {
        xAxis: {
          type: 'category',
          data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
        },
        yAxis: {
          type: 'value',
        },
        series: [
          {
            data: [150, 230, 224, 218, 135, 147, 260],
            type: 'line',
          },
        ],
      },
    };
    onMounted(() => {
      let autoSizeEchart = new AutoSizeEchart(options);
      autoSizeEchart.init();
    });

    const downloadPdf = () => {
      fy('te', '.box', 'p').then((res) => {
        alert(res);
      });
    };

    return {
      downloadPdf,
    };
  },
};
</script>

<template>
  <button class="ppp" @click="downloadPdf">{{ msg }}</button>
  <div class="box" id="chart1"></div>
  <div class="box" id="c1"></div>
  <div class="box" id="c1"></div>
</template>

<style scoped>
.box {
  /* border: 1px solid red; */
  width: 70vw;
  height: 40vw;
}
</style>
