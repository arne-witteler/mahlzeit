<script setup lang="ts">
import Map from './components/organisms/Map.vue';
import Sidebar from './components/organisms/Sidebar.vue';
</script>

<template>
  <div class="app-container">
    <Sidebar />
    <Map />
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app-container {
  display: flex;
  height: 100vh;
  padding: 0;
  margin: 0;
}
</style>
