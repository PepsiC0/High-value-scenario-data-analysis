<template>
  <div>
    <h1>GeoJSON Map</h1>
    <div ref="map" class="map-container"></div>
  </div>
</template>

<script>
import * as d3 from 'd3';

export default {
  mounted() {
    d3.json('/laneroad10.geojson')
        .then(geojsonData => {
          this.renderMap(geojsonData);
        })
        .catch(error => {
          console.error('Error fetching GeoJSON data:', error);
        });
  },
  methods: {
    renderMap(geojsonData) {
      const width  = this.$refs.map.clientWidth; // 地图容器宽度
      const height = 500; // 地图容器高度

      const svg = d3.select(this.$refs.map)
          .append('svg')
          .attr('width', width)
          .attr('height', height);

      const projection = d3.geoIdentity()
          .fitSize([width, height], geojsonData); // 根据数据调整投影范围 // 使用D3的geoIdentity投影，以保持相对坐标

      const path = d3.geoPath().projection(projection);

      const g = svg.append('g');

      g.selectAll('path')
          .data(geojsonData.features)
          .enter()
          .append('path')
          .attr('d', path)
          .style('stroke', 'white')
          .style('fill', 'none');

      // 添加拖动交互功能
      const dragHandler = d3.drag()
          .on('start', () => {
            // 记录拖动前的坐标
            const [x, y] = d3.pointer(event);
            g.attr('data-x', x);
            g.attr('data-y', y);
          })
          .on('drag', () => {
            // 获取拖动过程中的坐标变化
            const [x, y] = d3.pointer(event);
            const prevX = parseFloat(g.attr('data-x'));
            const prevY = parseFloat(g.attr('data-y'));
            const dx = x - prevX;
            const dy = y - prevY;

            // 更新地图位置
            g.attr('transform', `translate(${dx}, ${dy})`);
          });

      // 创建缩放行为
      const zoomBehavior = d3.zoom()
          .scaleExtent([1, 10]) // 设置缩放比例的范围
          .on('zoom', () => {
            g.attr('transform', d3.event.transform);
          });


      g.call(dragHandler);
      g.call(zoomBehavior);
    }
  }
}
</script>

<style>

.map-container {
  width: 100%;
  height: 500px;
}
</style>