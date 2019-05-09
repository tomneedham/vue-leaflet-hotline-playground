<template>
  <div id="app">
    <div style="height: 1000px; width: 100%">
      <l-map
      style="height: 80%; width: 100%"
      :zoom="zoom"
      :center="center"
      @update:zoom="zoomUpdated"
      @update:center="centerUpdated"
      @update:bounds="boundsUpdated"
      >
        <l-tile-layer :url="url"></l-tile-layer>
        <v-hotline :latlngs="latLngArray" :min="minValue" :max="maxValue"></v-hotline>
      </l-map>
    </div>
  </div>
</template>

<script>

import { LMap, LTileLayer } from 'vue2-leaflet'
import Vue2LeafletHotline from 'vue2-leaflet-hotline'

export default {
  name: 'app',
  components: {
    'l-map': LMap,
    'l-tile-layer': LTileLayer,
    'v-hotline': Vue2LeafletHotline
  },
  data () {
    return {
      url: 'http://{s}.tile.osm.org/{z}/{x}/{y}.png',
      zoom: 3,
      center: [47.413220, -1.219482],
      bounds: null,
      latLngArray: [[47.413220, -1.219482, 2], [47.413230, -1.219492, 2]]
    };
  },
  methods: {
    zoomUpdated (zoom) {
      this.zoom = zoom;
    },
    centerUpdated (center) {
      this.center = center;
    },
    boundsUpdated (bounds) {
      this.bounds = bounds;
    }
  }
}
</script>