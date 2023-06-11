<template>
  <div ref="chart" style="width: 100%; height: 350px;"></div>
</template>

<script>
import axios from 'axios';
import * as echarts from 'echarts';

export default {
  mounted() {
    this.getDataAndInitChart();
  },
  methods: {
    async getDataAndInitChart() {
      try {
        const response = await axios.get('/myTable.json');
        const rawData = response.data;
        this.initChart(rawData);
      } catch (error) {
        console.error('Failed to fetch data:', error);
      }
    },

    initChart(rawData) {
      const countries = [
        // 'Finland',
        // 'France',
        // 'Germany',
        // 'Iceland',
        // 'Norway',
        // 'Poland',
        // 'Russia',
        // 'United Kingdom',
        '急加速',
        '急减速',
        '非机动车',
        // '横穿马路',
        '切入切出'
      ];
      const datasetWithFilters = [];
      const seriesList = [];
      echarts.util.each(countries, function (country) {
        var datasetId = 'dataset_' + country;
        datasetWithFilters.push({
          id: datasetId,
          fromDatasetId: 'dataset_raw',
          transform: {
            type: 'filter',
            config: {
              and: [
                {dimension: 'Year', gte: 0},
                {dimension: 'Country', '=': country}
              ]
            }
          }
        });
        seriesList.push({
          type: 'line',
          datasetId: datasetId,
          showSymbol: false,
          name: country,
          endLabel: {
            show: true,
            formatter: function (params) {
              return params.value[1] + ': ' + params.value[0];
            }
          },
          labelLayout: {
            moveOverlap: 'shiftY'
          },
          emphasis: {
            focus: 'series'
          },
          encode: {
            x: 'Year',
            y: 'Income',
            label: ['Country', 'Income'],
            itemName: 'Year',
            tooltip: ['Income']
          }
        });
      });
      const xData = ['0:00', '2:00', '4:00', '6:00', '8:00', '10:00', '12:00', '14:00', '16:00', '18:00', '20:00', '22:00','24:00'];

      const option = {
        animationDuration: 10000,
        dataset: [
          {
            id: 'dataset_raw',
            source: rawData
          },
          ...datasetWithFilters
        ],
        title: {
          text: '不良交通参与行为数据分析',
          textStyle: {
            color: '#fff',
            fontSize: 20,
          },
          textAlign: 'auto',
          padding: 10,
        },
        tooltip: {
          order: 'valueDesc',
          trigger: 'axis'
        },

        xAxis: {
          type: 'category',
          name: '时间',
          data: xData,
          axisLine:{
              lineStyle:{
                color:'#fff'
              }
            },
          // axisLabel: {
          //   interval: 0,
          //   formatter: function (value, index) {
          //     if (index % 2 === 0) {
          //       return value;
          //     } else {
          //       return '\n' + value;
          //     }
          //   }
          // }
        },

        yAxis: {
          name: '数量',
          axisLine: {
            lineStyle: {
              color: '#fff'
            }
          }
        },
        grid: {
          right: 100,
          bottom: 85

        },
        series: seriesList
      };

      const myChart = echarts.init(this.$refs.chart);
      myChart.setOption(option);
    }
  }
};
</script>
