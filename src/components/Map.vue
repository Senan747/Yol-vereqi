<template>
  <div class="map" style="height: 75vh; width: 50vw">
    <l-map v-model="zoom" v-model:zoom="zoom" :center="[40.1431, 47.5769]">
      <l-tile-layer
        url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
      ></l-tile-layer>
      <l-control-layers />
      <l-marker :lat-lng="[40.6431, 49.4969]" draggable>
        <l-tooltip>Ford</l-tooltip>
      </l-marker>

      <l-marker :lat-lng="[40.3431, 49.9769]" draggable>
        <l-tooltip>Honda</l-tooltip>
      </l-marker>
      <l-marker :lat-lng="[40.3431, 49.3769]" draggable>
        <l-tooltip>Nissan</l-tooltip>
      </l-marker>
      <l-marker :lat-lng="[38.8431, 48.6769]" draggable>
        <l-tooltip>Toyota</l-tooltip>
      </l-marker>

      <l-marker :lat-lng="[41.1431, 46.9769]" draggable>
        <l-tooltip>Chevrolet</l-tooltip>
      </l-marker>

      <!-- <l-polyline
        :lat-lngs="[
          [47.334852, -1.509485],
          [47.342596, -1.328731],
          [47.241487, -1.190568],
          [47.234787, -1.358337],
        ]"
        color="green"
      ></l-polyline> -->
    </l-map>
  </div>
</template>
<script setup>
import {
  LMap,
  LIcon,
  LTileLayer,
  LMarker,
  LControlLayers,
  LTooltip,
  LPopup,
  LPolyline,
  LPolygon,
  LRectangle,
} from "@vue-leaflet/vue-leaflet";
import "leaflet/dist/leaflet.css";
import { ref } from "vue";

const zoom = ref(6.7);
const iconWidth = ref(25);
const iconHeight = ref(40);
</script>

<style scoped>
.map {
  height: 75vh;
  width: 50vw;
}
</style>
