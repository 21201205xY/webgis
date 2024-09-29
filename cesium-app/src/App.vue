<template>
  <div id="cesiumContainer"></div>
</template>

<script setup>
import * as Cesium from 'cesium';
import { onMounted, readonly } from 'vue';

onMounted(()=>{
  // const viewer = new Cesium.Viewer('cesiumContainer');
  var custom = new Cesium.ArcGisMapServerImageryProvider({
    url:'//services.arcgisonline.com/ArcGIS/rest/services/World_Street_Map/MapServer'
  })

  var customTerrainProvider = new Cesium.EllipsoidTerrainProvider({
      ready:true,
      hasVertexNormals:true,
      hasWaterMask:true,
  })

  var viewer = new Cesium.Viewer('cesiumContainer',{
    animation:false,
    baseLayerPicker:false,
    imageryProvider:new Cesium.ArcGisMapServerImageryProvider({
      url: 
        'https://services.arcgisonline.com/ArcGIS/rest/services/World_Street_Map/MapServer',
    }),
    imageryProvider:custom,
    terrainProvider:customTerrainProvider,
  })
})
</script>

<style scoped>

</style>
 