<template>
  <!-- 第三行 -->
  <div class="module-box ">
    <div style="flex:0 1 50%">
      <dv-border-box-8 style="width:100%;height:300px;">
        <dv-scroll-board :config="config5" style="width:100%;height:280px" />
      </dv-border-box-8>
    </div>
    <div style="flex:0 1 50%">
      <dv-border-box-8 style="width:100%;height:280px;">
        <Chart5 />
      </dv-border-box-8>
    </div>

  </div>
</template>

<script>
import JiaoNang from "@/views/JiaoNang.vue";
import Chart4 from "@/views/Chart4";
import Chart from "@/views/Chart";
import Chart2 from "@/views/Chart2";
import Chart3 from "@/views/Chart3";
import Map from "@/views/Map";
import Chart5 from "@/views/Chart5";

export default {
  components:{
    Chart4,
    Chart,
    Chart2,
    Chart3,
    Map,
    JiaoNang,
    Chart5,
  },
  data(){
    return {
      config5:{
        header: ['不良交通行为', 'ID', '时间'],
        data: [
          ['行人横穿马路', '175479177', '2023/4/13  0:24:00'],
          ['行人横穿马路', '175952670', '2023/4/13  0:35:00'],
          ['行人横穿马路', '177446064', '2023/4/13  1:08:00'],
          ['非机动车斜穿马路', '177497691', '2023/4/13  1:09:31'],
          ['非机动车斜穿马路', '188450903', '2023/4/13  5:38:11'],
          ['非机动车斜穿马路', '189382933', '2023/4/13  5:54:25'],
          ['车辆急加速', '189427106', '2023/4/13  5:55:11'],
          ['车辆急加速', '189659654', '2023/4/13  5:59:25'],
          ['车辆急加速', '189993864', '2023/4/13  6:05:18'],
          ['车辆切入切出', '195429720', '2023/4/13  7:09:40'],
          ['车辆切入切出', '195503645', '2023/4/13  7:10:19'],
          ['车辆切入切出', '198264220', '2023/4/13  7:29:27']
        ],
        index: true,
        columnWidth: [50],
        align: ['center']
      }
    }
  }
}
</script>
