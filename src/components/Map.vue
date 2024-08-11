<template>
  <div ref="mapContainer" class="map-container"></div>
</template>

<script lang="js">
import { defineComponent, ref } from 'vue';
import mapboxgl from 'mapbox-gl';
import "mapbox-gl/dist/mapbox-gl.css";


export default defineComponent({
  name: 'MapComponent',
  mounted() {

    const map = new mapboxgl.Map({
      container: this.$refs.mapContainer,
      style: "https://api.parsimap.ir/styles/parsimap-streets-v11?key=YOUR_PARSIMAP_TOKEN",
      center: [51.37669, 35.73020],
      zoom: 9,
    });
    this.map = map;


    function addRTLPlugin() {
      if (mapboxgl.getRTLTextPluginStatus() !== "unavailable") return;
      mapboxgl.setRTLTextPlugin("https://cdn.parsimap.ir/third-party/mapbox-gl-js/plugins/mapbox-gl-rtl-text/v0.2.3/mapbox-gl-rtl-text.js", (error) => {
        if (error) {
          console.error('Failed to load RTL plugin: ', error);
        }
      });
    }

    addRTLPlugin();
  },

  setup() {
    const mapContainer = ref < HTMLDivElement | null > (null);
    return {
      mapContainer,
    };
  },
});
</script>

<style scoped>
.map-container {
  width: 100vw;
  height: 100vh;
}
</style>
