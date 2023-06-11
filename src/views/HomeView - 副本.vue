<template>
  <div class="content bg">
    <!-- 全屏容器 -->
    <dv-full-screen-container>
      <!-- 第一行 -->
      <div class="module-box ">
        <div style="flex:0 1 30%">
          <dv-decoration-10 style="height:10px;" />
        </div>
        <div style="flex:0 1 40%">
          <div class="d-flex">
            <dv-decoration-8 style="height:10px;flex:1;" />
            <dv-decoration-7 style="height:30px;" class="center-title">高价值场景数据分析</dv-decoration-7>
            <dv-decoration-8 :reverse="true" style="height:10px;flex:1;" />
          </div>
        </div>
        <div style="flex:0 1 30%">
          <dv-decoration-10 style="height:10px;transform:rotateY(180deg)" />
        </div>
      </div>


      <!-- 第二行 -->
      <div class="module-box ">
        <!-- 左 -->
        <div style="flex:0 1 25%">
          <dv-border-box-1 style="width:100%;height:500px;">
            <dv-scroll-board :config="config5" style="width:100%;height:500px" />
          </dv-border-box-1>
        </div>
        <!-- 中 -->
        <div style="flex:0 1 25%">
          <dv-border-box-2 style="width:100%;height:300px;">
            <dv-active-ring-chart :config="config1" style="height:300px" />
          </dv-border-box-2>
          <dv-border-box-3 style="width:100%;height:200px;">
            <dv-water-level-pond :config="config3" style="width:100%;height:200px" />
          </dv-border-box-3>
        </div>
        <!-- 中 -->
        <div style="flex:0 1 25%">
          <dv-border-box-4 style="width:100%;height:300px;">
            <dv-water-level-pond :config="config3" style="width:100%;height:300px" />
          </dv-border-box-4>
          <dv-border-box-5 style="width:100%;height:200px;">
            <dv-water-level-pond :config="config3" style="width:100%;height:200px" />
          </dv-border-box-5>
        </div>
        <!-- 右 -->
        <div style="flex:0 1 25%">
          <dv-border-box-6 style="width:100%;height:200px;">
            <dv-water-level-pond :config="config3" style="width:100%;height:200px" />
          </dv-border-box-6>
          <dv-border-box-7 style="width:100%;height:300px;">
            <dv-scroll-ranking-board :config="config1" style="height:300px" />
          </dv-border-box-7>
        </div>
      </div>

      <!-- 第三行 -->
      <div class="module-box ">
        <div style="flex:0 1 50%">
          <dv-border-box-8 style="width:100%;height:200px;">
            <dv-capsule-chart :config="config1" style="width:100%;height:200px" />
          </dv-border-box-8>
        </div>
        <div style="flex:0 1 25%">
          <dv-border-box-9 style="width:100%;height:200px;">
            <dv-capsule-chart :config="config1" style="width:100%;height:200px" />
          </dv-border-box-9>
        </div>
        <div style="flex:0 1 25%">
          <dv-border-box-10 style="width:100%;height:200px;">
            <dv-water-level-pond :config="config3" style="width:100%;height:200px" />
          </dv-border-box-10>
        </div>
      </div>

    </dv-full-screen-container>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
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
      config4:{
        centerPoint: [0.48, 0.35],
        points: [
          [0.52, 0.23],
          [0.43, 0.29],
          [0.59, 0.35],
          [0.53, 0.47],
          [0.45, 0.54],
          [0.36, 0.38],
          [0.62, 0.55],
          [0.56, 0.56],
          [0.37, 0.66],
          [0.55, 0.81],
          [0.55, 0.67],
          [0.37, 0.29],
          [0.20, 0.36],
          [0.76, 0.41],
          [0.59, 0.18],
          [0.68, 0.17],
          [0.59, 0.10]
        ],
        bgImgUrl: require('../assets/img/map.jpg'),
        flylineColor:'#fff',
        centerPointImg: {
          url:  require('../assets/img/mapCenterPoint.png')
        },
        pointsImg: {
          url:  require('../assets/img/mapPoint.png')
        }
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
