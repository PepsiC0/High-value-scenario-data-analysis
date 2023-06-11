<template>
  <!-- 第一行 -->
<!--  <div class="module-box ">-->
<!--    <div style="flex:0 1 30%">-->
<!--      <dv-decoration-10 style="height:10px;" />-->
<!--    </div>-->
<!--    <div style="flex:0 1 40%">-->
<!--      <div class="d-flex">-->
<!--        <dv-decoration-8 style="height:10px;flex:1;" />-->
<!--        <dv-decoration-7 style="height:30px;" class="center-title">高价值场景数据分析</dv-decoration-7>-->
<!--        <dv-decoration-8 :reverse="true" style="height:10px;flex:1;" /></div>-->
<!--    </div>-->
<!--    <div style="flex:0 1 30%">-->
<!--      <dv-decoration-10 style="height:10px;transform:rotateY(180deg)" />-->
<!--    </div>-->
<!--  </div>-->
  <div id="top-header">
    <dv-decoration-8 class="header-left-decoration" />
    <dv-decoration-5 class="header-center-decoration" />
    <dv-decoration-8 class="header-right-decoration" :reverse="true" />
    <div class="center-title">高价值场景数据可视化分析</div>
  </div>
</template>

<script>
import TitleChart from "@/views/TitleChart";

export default {
  name: 'ModuleTitle',
  components:{
      TitleChart,
  }
}
</script>

<style lang="less">
#top-header {
  position: relative;
  width: 100%;
  height: 80px;
  display: flex;
  justify-content: space-between;
  flex-shrink: 0;

  .header-center-decoration {
    width: 40%;
    height: 60px;
    margin-top: 30px;
  }

  .header-left-decoration, .header-right-decoration {
    width: 25%;
    height: 60px;
  }

  .center-title {
    position: absolute;
    font-size: 30px;
    font-weight: bold;
    left: 50%;
    top: 15px;
    transform: translateX(-50%);
  }
}
</style>