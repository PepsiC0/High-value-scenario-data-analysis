<template>
  <!-- 为 ECharts 准备一个定义了宽高的 DOM -->
  <div ref="chart" style="width: 100%;height:100%;"></div>
</template>

<script>
import * as echarts from 'echarts'

export default {
  data(){
    return{

    }
  },
  mounted() {
    this.initChart();

  },
  methods:{
    initChart(){
      // 基于准备好的dom，初始化echarts实例
      const myChart = echarts.init(this.$refs.chart);

      var option;

      option = {
        graphic: {
          elements: [
            {
              type: 'text',
              // left: 'center',
              top: '10%',
              style: {
                text: '高价值场景数据可视化分析',
                fontSize: 45,
                fontWeight: 'bold',
                lineDash: [0, 200],
                lineDashOffset: 0,
                fill: 'transparent',
                stroke: '#fff',
                lineWidth: 1
              },
              keyframeAnimation: {
                duration: 3000,
                loop: true,
                keyframes: [
                  {
                    percent: 0.7,
                    style: {
                      fill: 'transparent',
                      lineDashOffset: 200,
                      lineDash: [200, 0]
                    }
                  },
                  {
                    // Stop for a while.
                    percent: 0.8,
                    style: {
                      fill: 'transparent'
                    }
                  },
                  {
                    percent: 1,
                    style: {
                      fill: 'white'
                    }
                  }
                ]
              }
            }
          ]
        }
      };

      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
    },
  }
}
</script>