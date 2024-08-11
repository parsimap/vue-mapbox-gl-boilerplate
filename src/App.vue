<template>
  <div id="app">
    <MapComponent />
  </div>
</template>

<script lang="js">
import { defineComponent } from 'vue';
import MapComponent from './components/Map.vue';

export default defineComponent({
  name: 'App',
  components: {
    MapComponent,
  },
});
</script>
<style>
body{
  margin: 0;
}
</style>
