<template>
  <div class="map-page">
    <div id="map">
    </div>
  </div>
</template>

<script>
import {Scene, PointLayer, LineLayer} from '@antv/l7';
import { GaodeMap } from '@antv/l7-maps';
import axios from 'axios';

export default {
  data() {
    return {}
  },
  mounted() {
    this.initScene();
  },
  methods: {
    initScene() {
      // 基于准备好的dom，初始化echarts实例
      const scene = new Scene({
        id: 'map',
        map: new GaodeMap({
          center: [-74.006, 40.7128],
          zoom: 14,
          style: 'dark'
        })
      });
      scene.on('loaded', () => {
        axios.get('/FeHelper-20230608150832.json') // 修改路径为正确的文件路径
            .then(response => {
              const data = response.data;
              const lineLayer = new LineLayer()
                  .source(data, {
                    parser: {
                      type: 'json',
                      coordinates: 'path'
                    }
                  })
                  .size(3)
                  .shape('line')
                  .color('color', v => {
                    return `rgb(${v})`;
                  })
                  .animate({
                    interval: 0.6,
                    trailLength: 0.5,
                    duration: 6
                  });
              scene.addLayer(lineLayer);
            })
            .catch(error => {
              console.error('Error loading GeoJSON file:', error);
            });
      });
    },
  },

}

</script>



