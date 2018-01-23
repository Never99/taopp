<template>
  <div class="chart-area">
    <div id="myChart"></div>
  </div>
</template>

<script>
// 引入基本模板
let echarts = require('echarts/lib/echarts')
// 引入柱状图组件
require('echarts/lib/chart/line')
// 引入提示框和title组件
require('echarts/lib/component/tooltip')
require('echarts/lib/component/title')
export default {
  data() {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  mounted() {
    this.drawLine();
  },
  methods: {
    drawLine() {
      let myChart = echarts.init(document.getElementById('myChart'))
      let colors = ['#5793f3', '#d14a61', '#675bba']

      myChart.setOption({
        title: { text: '' },
        color: colors,
        tooltip: {
          trigger: 'none',
          axisPointer: {
            type: 'cross'
          }
        },
        legend: {},
        grid: {
          top: 50,
          bottom: 50
        },
        xAxis: [{
          type: 'category',
          axisTick: {
            alignWithLabel: true
          },
          axisLine: {
            onZero: false,
            lineStyle: {
              color: colors[1]
            }
          },
          axisPointer: {
            label: {
              formatter: function(params) {
                return '2017-' + params.value +
                  (params.seriesData.length ? '：' + params.seriesData[0].data : '') + '亿票房';
              }
            }
          },
          data: ["09-08", "09-09", "09-10", "09-11", "09-12", "09-13", "09-14", "09-15", "09-16", "09-17", "09-18", "09-19", "09-20", "09-21", "09-22", "09-23", "09-24", "09-25", "09-26"]
        }],
        yAxis: [{
          type: 'value'
        }],
        series: [{

          type: 'line',
          smooth: true,
          data: [1.340, 1.850, 1.330, 0.41438, 0.33741, 0.48013, 0.43371, 0.40478, 0.43176, 0.41121, 0.40142, 0.40062, 0.40037, 0.30026, 0.30001984, 0.30004239, 0.2001308, 0.1, 0]
        }]
      });
      return myChart
    }
  }
}
</script>

<style lang="less" scoped>
.chart-area {
  width: 100%;

  #myChart {
    width: 90%;
    height: 3rem;
    margin: 0 auto;
    canvas {
      width: 100%!important;
    }
  }
}
</style>

