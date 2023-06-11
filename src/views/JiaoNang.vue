<template>
  <div id="JiaoNang">
    <div class="JiaoNang-title">统计分析</div>
    <dv-capsule-chart :config="config1" style="width:100%;height:100%" />
  </div>
</template>

<script>
export default {
  props:{
    colorsChart:{
      type:Array,
      default:()=>['#e062ae', '#fb7293', '#e690d1', '#32c5e9', '#96bfff'],
    },
    dataChart:{
      type:Array,
      default:()=>[
        {
          name: '南阳',
          value: 20
        },
        {
          name: '周口',
          value: 67
        },
        {
          name: '漯河',
          value: 123
        },
        {
          name: '郑州',
          value: 55
        },
        {
          name: '西峡',
          value: 98
        }
      ]
    }
  },
  data() {
    return {
      config1: {
        data: this.dataChart,
        colors: this.colorsChart,
        unit: '',
        showValue: true
      }
    }
  }
}
</script>

<style lang="less">
#JiaoNang {
  width: 100%;
  height: 100%;

  .JiaoNang-title {
    height: 30px;
    font-weight: bold;
    text-indent: 20px;
    font-size: 20px;
    display: flex;
    align-items: center;
  }
}
</style>
