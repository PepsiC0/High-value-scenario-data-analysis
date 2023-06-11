<template>
  <div class="content bg">
    <!-- 全屏容器 -->
    <dv-full-screen-container>
      <ModuleTitle />
      <ModuleMain />
      <ModuleFooter />

    </dv-full-screen-container>
  </div>
</template>

<script>
import ModuleTitle from './ModuleTitle.vue'
// import ModuleHeader from './ModuleHeader.vue'
import ModuleMain from './ModuleMain.vue'
import ModuleFooter from './ModuleFooter.vue'


export default {
  name: 'HomeView',
  components:{
    ModuleTitle,
    ModuleMain,
    ModuleFooter,
  }
}
</script>
