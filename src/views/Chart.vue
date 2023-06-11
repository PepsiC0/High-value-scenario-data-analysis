<!--三列一图-->
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
  // legend: {
  //   top: 'bottom'
  // },
  // toolbox: {
  //   show: true,
  //   feature: {
  //     mark: { show: true },
  //     dataView: { show: true, readOnly: false },
  //     restore: { show: true },
  //     saveAsImage: { show: true }
  //   }
  // },
        title: {
            text: '不良交通参与行为占比',
            textStyle:{
              color: '#fff',
              fontSize: 20,
            },
            textAlign:'auto',
            padding: 10,

          },
        grid:{
            left:'5%',
            right:'5%',
            top:'60%',
            bottom:'5%',
            containLabel:true,
          },
  series: [
    {
      name: 'Nightingale Chart',
      type: 'pie',
      radius: [50, 120],
      center: ['50%', '55%'],
      roseType: 'area',
      itemStyle: {
        borderRadius: 10
      },
      data: [
        { value: 13306, name: '车辆急加速' },
        { value: 14524, name: '车辆急减速' },
        { value: 17080, name: '行人横穿马路' },
        { value: 5130, name: '非机动车斜穿马路' },
        { value: 28471, name: '车辆切入切出' }
      ]
    }
  ]
};

option && myChart.setOption(option);
    },
  }
}
</script>