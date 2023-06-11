<template>
  <!-- 第二行 -->
  <div class="module-box ">
    <!-- 左 -->
    <div style="flex:0 1 25%">
      <dv-border-box-10 style="width:100%;height:280px;">
        <Chart />
      </dv-border-box-10>
      <dv-border-box-10 style="width:100%;height:280px;">
        <Chart2 />
      </dv-border-box-10>
    </div>
    <!-- 中 -->
    <div style="flex:0 1 50%">
      <dv-border-box-8 style="width:100%;height:560px;">
        <Map2 />
      </dv-border-box-8>
    </div>

    <!-- 右 -->
    <div style="flex:0 1 25%">
      <dv-border-box-10 style="width:100%;height:560px;">
        <Chart3 />
      </dv-border-box-10>

    </div>
  </div>
</template>

<script>
import Chart from "@/views/Chart";
import Chart2 from "@/views/Chart2"
import Chart3 from "@/views/Chart3";
import Map from "@/views/Map";
import GeoJSON from "@/views/GeoJson"
import Map2 from "@/views/Map2";
import Map3 from "@/views/Map3";

export default {
  components:{
    Chart,
    Chart2,
    Chart3,
    Map,
    GeoJSON,
    Map2,
    Map3,
  },
  data(){
    return {
      config1:{
        data: [
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
      },
      config2:{
        data: [
          {
            name: '南阳',
            value: 167
          },
          {
            name: '周口',
            value: 123
          },
          {
            name: '漯河',
            value: 98
          },
          {
            name: '郑州',
            value: 75
          },
          {
            name: '西峡',
            value: 66
          },
        ],
        colors: ['#e062ae', '#fb7293', '#e690d1', '#32c5e9', '#96bfff'],
        unit: '单位',
        showValue: true
      },
      config3:{
        data: [66, 45],
        shape: 'roundRect',
        colors:['#f60','green'],
        waveOpacity:0.2
      },
      config5:{
        header: ['列1', '列2', '列3'],
        data: [
          ['行1列1', '行1列2', '行1列3'],
          ['行2列1', '行2列2', '行2列3'],
          ['行3列1', '行3列2', '行3列3'],
          ['行4列1', '行4列2', '行4列3'],
          ['行5列1', '行5列2', '行5列3'],
          ['行6列1', '行6列2', '行6列3'],
          ['行7列1', '行7列2', '行7列3'],
          ['行8列1', '行8列2', '行8列3'],
          ['行9列1', '行9列2', '行9列3'],
          ['行10列1', '行10列2', '行10列3']
        ]
      }
    }
  }
}
</script>
