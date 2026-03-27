<script setup lang="ts">
import { ref, onMounted } from 'vue';
import L from 'leaflet';
import { LMap, LTileLayer, LMarker, LPopup } from "@vue-leaflet/vue-leaflet";

import "leaflet/dist/leaflet.css";

const zoom = ref(13);
const center = ref<[number, number]>([52.5200, 13.4050]); // Berlin Mitte
const url = "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png";

onMounted(() => {
  delete (L.Icon.Default.prototype as any)._getIconUrl;
  L.Icon.Default.mergeOptions({
    iconRetinaUrl: 'https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/images/marker-icon-2x.png',
    iconUrl: 'https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/images/marker-icon.png',
    shadowUrl: 'https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/images/marker-shadow.png',
  });
});
</script>

<template>
  <div class="map-container">
    <l-map v-model:zoom="zoom" :center="center" :use-global-leaflet="false">
      <l-tile-layer :url="url" layer-type="base" name="OpenStreetMap"></l-tile-layer>
    </l-map>
  </div>
</template>

<style scoped>
.map-container {
  height: 100vh;
  width: 100%;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

:deep(.leaflet-container) {
  height: 100%;
  width: 100%;
}
</style>