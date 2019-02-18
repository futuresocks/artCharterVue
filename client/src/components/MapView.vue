<template lang="html">
  <div id="mapContainer"></div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'mapView',
  props: ['murals'],
  data(){
    return {
      osmLayer: new L.TileLayer("http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"),
      map: null,
      markers: []
    }
  },
  mounted(){
    this.map = L.map('mapContainer')
    .setView([55.8642, -4.2518], 16)
    .addLayer(this.osmLayer);
  },
  watch: {
    murals: function(murals){
      murals.forEach((mural, index) => {
        L.marker(mural.coords)
        .addTo(this.map)
        .on('click', () => eventBus.$emit('marker-clicked', index))
      })
    }
  }
}
</script>

<style lang="css" scoped>
#mapContainer{
  width:500px;
  height:500px;
}
</style>
