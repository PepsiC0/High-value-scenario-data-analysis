<template>
  <div id="map"></div>
</template>

<script>
import L from 'leaflet';
import axios from 'axios';
export default {
  mounted() {
    // 初始化地图
    this.map = L.map('map').setView([51.505, -0.09], 13);

    // 添加瓷砖图层
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution: 'Map data &copy; OpenStreetMap contributors'
    }).addTo(this.map);

    // 加载并添加GeoJSON数据
    axios.get('/laneroad10.geojson') // 修改路径为正确的文件路径
        .then(response => {
          const data = response.data;
          L.geoJSON(data).addTo(this.map);
        })
        .catch(error => {
          console.error('Error loading GeoJSON file:', error);
        });
  }
}
</script>

<style>
#map {
  height: 400px;
}
</style>
