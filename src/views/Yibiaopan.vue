<!--三列二图-->
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
      const dataname = ["德", "智（一）", "智（二）", "体", "美", "劳"];
      const datamax = [20, 20, 20, 20, 20, 20];
      const datavaule = [9, 16, 16, 15, 12, 8];
      const datavaule1 = [6, 8, 10, 6, 5, 8];
      const datavaule2 = [19, 19, 19, 19, 19, 19];

      const indicator = [];
      for (let i = 0; i < dataname.length; i++) {
        indicator.push({
          name: dataname[i],
          max: datamax[i],
        });
      }
      let option;

      option = {
        title: {
          text: '雷达图',
          textStyle:{
            color: '#fff',
            fontSize: 20,
          },
          textAlign:'auto',
          padding: 15,
        },
        tooltip: {
          show: true,
          trigger: "item",
        },
        legend: {
          data: ["当前分数", "均值", "满分"],
          type: "scroll",
          orient: "vertical",
          icon: "roundRect",
          right: "20",
          top: "center",
          itemGap: 30,
          itemWidth: 16,
          itemHeight: 16,
          textStyle: {
            fontSize: "15",
            color: "#FFF",
          },
        },
        radar: {
          center: ["50%", "50%"],
          radius: "65%",
          startAngle: 90,
          splitNumber: 5,
          splitArea: {
            areaStyle: {
              color: ["#FFFFFF", "#F5F9FF"].reverse(),
            },
          },
          axisLabel: {
            show: false,
          },
          axisLine: {
            show: true,
            lineStyle: {
              color: "#D2E4F8",
            },
          },
          splitLine: {
            show: true,
            lineStyle: {
              color: "#D2E4F8",
            },
          },
          name: {
            formatter: "{value}",
            textStyle: {
              color: "#FFF",
              fontSize: 18,
            },
          },
          indicator: indicator,
        },

        series: [
          {
            name: "当前分数",
            type: "radar",
            symbol: "none",
            symbolSize: 6,
            areaStyle: {
              normal: {
                color: "#80B2FF",
              },
            },
            itemStyle: {
              color: "#80B2FF",
            },
            lineStyle: {
              normal: {
                color: "#80B2FF",
                width: 2,
              },
            },
            data: [datavaule],
          },
          {
            name: "均值",
            type: "radar",
            symbol: "none",
            symbolSize: 6,
            /*areaStyle: {
                  normal: {
                      color: 'rgba(103, 193, 57, 0.18)',
                  }
              },*/
            itemStyle: {
              color: "#FF7A28",
            },
            lineStyle: {
              normal: {
                color: "#FF7A28",
                width: 2,
              },
            },
            data: [datavaule1],
          },
          {
            name: "满分",
            type: "radar",
            symbol: "none",
            symbolSize: 6,
            /*areaStyle: {
                  normal: {
                      color: 'rgba(234, 164, 61, 0.18)',
                  }
              },*/
            itemStyle: {
              color: "#0263FF",
            },
            lineStyle: {
              normal: {
                color: "#0263FF",
                width: 2,
              },
            },
            data: [datavaule2],
          },
        ],
      };

      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
    },
  }
}
</script>