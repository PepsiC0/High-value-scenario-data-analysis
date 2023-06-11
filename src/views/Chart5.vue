<template>
  <!-- 为 ECharts 准备一个定义了宽高的 DOM -->
  <div ref="chart" style="width: 100%;height:100%;"></div>
</template>

<script>
import * as echarts from 'echarts'

export default {
  data() {
    return {}
  },
  mounted() {
    this.initChart();

  },
  methods: {
    initChart() {
      // 基于准备好的dom，初始化echarts实例
      const myChart = echarts.init(this.$refs.chart);

      var option;

      const categories = (function () {
        // let now = new Date();
        let res = ['0:00', '2:00', '4:00', '6:00', '8:00', '10:00', '12:00', '14:00', '16:00', '18:00', '20:00', '22:00'];
        // let len = 10;
        // while (len--) {
        //   res.unshift(now.toLocaleTimeString().replace(/^\D*/, ''));
        //   now = new Date(+now - 2000);
        // }
        return res;
      })();
      const categories2 = (function () {
        let res = ['0:00', '2:00', '4:00', '6:00', '8:00', '10:00', '12:00', '14:00', '16:00', '18:00', '20:00', '22:00'];

        // let len = 10;
        // while (len--) {
        //   res.push(10 - len - 1);
        // }
        return res;
      })();
      const data = (function () {
        let res = [11.1819701895947933, 4.80798981211418611, 11.38432100824704494, 150.3295655918179146, 241.665158708002078, 156.584851557004266, 154.608938646890563, 164.237780793872446, 197.556800911068606, 146.191195751107874, 96.958939525487979, 50.5050094334259164];
        // let len = 10;
        // while (len--) {
        //   res.push(Math.round(Math.random() * 1000));
        // }
        return res;
      })();
      const data2 = (function () {
        let res = [179.483657836593312, 174.303162567069274, 208.933669859812656, 240.818959168654582, 224.488221458953018, 192.480981224172454, 193.528148285304356, 202.014109532314803, 205.977897385786755, 196.456354616499623, 202.576735258439329, 203.409743962464382];
        // let len = 0;
        // while (len < 10) {
        //   res.push(+(Math.random() * 10 + 5).toFixed(1));
        //   len++;
        // }
        return res;
      })();
      option = {
        title: {
          text: '道路拥堵情况和流量数据分析',
          textStyle: {
            color: '#fff',
            fontSize: 20,
          },
          textAlign: 'auto',
          padding: 10,

        },
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'cross',
            label: {
              backgroundColor: '#283b56'
            }
          }
        },
        legend: {},
        toolbox: {
          show: false,
          feature: {
            dataView: {readOnly: false},
            restore: {},
            saveAsImage: {}
          }
        },
        dataZoom: {
          show: false,
          start: 0,
          end: 100
        },
        xAxis: [
          {
            type: 'category',
            boundaryGap: true,
            data: categories,
            axisLine: {
              lineStyle: {
                color: '#fff'
              }
            },
            axisTick: {
              alignWithLabel: true  // 设置刻度与标签对齐
            }
          },
          {
            type: 'category',
            // boundaryGap: true,
            // data: categories2,
            // axisLine: {
            //   lineStyle: {
            //     color: '#fff'
            //   }
            // },
            axisTick: {
              alignWithLabel: true  // 设置刻度与标签对齐
            }
          }
        ],

        yAxis: [
          {
            type: 'value',
            scale: true,
            name: '流量情况',
            max: 300,
            min: 0,
            boundaryGap: [0.2, 0.2],
            axisLine: {
              lineStyle: {
                color: '#fff'
              }
            }
          },
          {
            type: 'value',
            scale: true,
            name: '拥堵指标',
            max: 300,
            min: 0,
            boundaryGap: [0.2, 0.2],
            axisLine: {
              lineStyle: {
                color: '#fff'
              }
            }
          }
        ],

        series: [
          {
            type: 'bar',
            xAxisIndex: 0,  // 绑定到第一个 x 轴
            yAxisIndex: 0,
            data: data,
            barCategoryGap: '50%',  // 设置柱状图间隔
            itemStyle: {
              normal: {
                color: function (params) {
                  if (params.data < 30)
                    return '#ff0000'
                  else if (params.data < 50)
                    return '#ff6100'
                  else if (params.data < 70)
                    return '#e3cf57'
                  else if (params.data < 90)
                    return '#308014'
                  else
                    return '#2ec7c9'
                }
              }
            }
          },
          {
            type: 'line',
            xAxisIndex: 1,  // 绑定到第二个 x 轴
            yAxisIndex: 1,
            data: data2,
            itemStyle: {
              normal: {
                color: function (params) {
                  return '#ffd700'
                }
              }
            },
            lineStyle: {
              color: '#ffd700'
            }
          }
        ],


        grid: {
          left: '5%',
          right: '5%',
          top: '15%',
          bottom: '5%',
          containLabel: true,
        }
      };
      app.count = 11;
      setInterval(function () {
        let axisData = new Date().toLocaleTimeString().replace(/^\D*/, '');
        // data.shift();
        // data.push(Math.round(Math.random() * 1000));
        // data2.shift();
        // data2.push(+(Math.random() * 10 + 5).toFixed(1));
        // categories.shift();
        // categories.push(axisData);
        // categories2.shift();
        // categories2.push(app.count++);
        myChart.setOption({
          xAxis: [
            {
              data: categories
            },
            {
              data: categories2
            }
          ],
          series: [
            {
              data: data
            },
            {
              data: data2
            }
          ]
        });
      }, 2100);

      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
    },
  }
}
</script>