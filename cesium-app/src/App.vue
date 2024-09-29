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

  var viewer = new Cesium.Viewer('cesiumContainer',{
    animation:false,
    baseLayerPicker:false,
    imageryProvider:new Cesium.ArcGisMapServerImageryProvider({
      url: 
        'https://services.arcgisonline.com/ArcGIS/rest/services/World_Street_Map/MapServer',
    }),
    imageryProvider:custom,
    terrain: Cesium.Terrain.fromWorldTerrain({
    requestWaterMask: true,
    requestVertexNormals: true,
    }),
  })

  viewer.scene.setTerrain(
    new Cesium.Terrain(
      Cesium.ArcGISTiledElevationTerrainProvider.fromUrl(
        "https://elevation3d.arcgis.com/arcgis/rest/services/WorldElevation3D/Terrain3D/ImageServer"
      )
    )
  );

})
</script>

<style scoped>

</style>
 