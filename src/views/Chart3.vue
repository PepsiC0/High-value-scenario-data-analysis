<!--二列一图-->
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
  methods: {
    initChart() {
      // 基于准备好的dom，初始化echarts实例
      const myChart = echarts.init(this.$refs.chart);

      let option;

      setTimeout(function () {
        option = {
          title: {
            text: '行人横穿马路数据分析',
            textStyle:{
              color: '#fff',
              fontSize: 20,
            },
            textAlign:'auto',
            padding: 10,

          },
          // legend: {},
          tooltip: {
            trigger: 'axis',
            showContent: false
          },
          dataset: {
            source: [
              ['product', '0:00',  '4:00',  '8:00',  '12:00',  '16:00',  '20:00', '24:00'],
              ['路口一', 560.5, 820.1, 880.7, 700.1, 530.4, 805.1,560.5],
              ['路口二', 510.1, 510.4, 550.1, 530.3, 730.8, 680.7,510.1],
              ['路口三', 400.1, 620.2, 690.5, 360.4, 450.2, 320.5,400.1],
              ['路口四', 250.2, 370.1, 410.2, 180, 330.9, 490.1,250.2]
            ]
          },
          xAxis: {
            type: 'category',
            axisLine:{
              lineStyle:{
                color:'#fff'
              }
            }
          },
          yAxis: {
            gridIndex: 0,
            axisLine: {
              lineStyle: {
                color: '#fff'
              }
            }
          },
          grid:{
            left:'5%',
            right:'5%',
            top:'50%',
            bottom:'5%',
            containLabel:true,
          },
          series: [
            {
              type: 'line',
              smooth: true,
              seriesLayoutBy: 'row',
              emphasis: {focus: 'series'}
            },
            {
              type: 'line',
              smooth: true,
              seriesLayoutBy: 'row',
              emphasis: {focus: 'series'}
            },
            {
              type: 'line',
              smooth: true,
              seriesLayoutBy: 'row',
              emphasis: {focus: 'series'}
            },
            {
              type: 'line',
              smooth: true,
              seriesLayoutBy: 'row',
              emphasis: {focus: 'series'}
            },
            {
              type: 'pie',
              id: 'pie',
              radius: '25%',
              center: ['50%', '25%'],
              emphasis: {
                focus: 'self'
              },
              label: {
                formatter: '{b}: {@2012} ({d}%)'
              },
              encode: {
                itemName: 'product',
                value: '0:00',
                tooltip: '0:00'
              }
            }
          ],

        };
        myChart.on('updateAxisPointer', function (event) {
          const xAxisInfo = event.axesInfo[0];
          if (xAxisInfo) {
            const dimension = xAxisInfo.value + 1;
            myChart.setOption({
              series: {
                id: 'pie',
                label: {
                  formatter: '{b}: {@[' + dimension + ']} ({d}%)'
                },
                // encode: {
                //   value: dimension,
                //   tooltip: dimension
                // }
              }
            });
          }
        });

        // 使用刚指定的配置项和数据显示图表。
        myChart.setOption(option);
      });
      option && myChart.setOption(option);
    }
  }
}
</script>