<template lang="html">
    <div id="mapContainer"></div>
</template>

<script>
export default {
  data(){
    return {
      osmLayer: new L.TileLayer("http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"),
      map: null
    }
  },
  mounted(){
    this.map = L.map('mapContainer')
              .setView([0,0], 2)
              .addLayer(this.osmLayer)
  }
}
</script>

<style lang="css">
#mapContainer{
  width:500px;
  height:500px;
}
</style>
