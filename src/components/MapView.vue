<template lang="html">
  <div id="mapContainer"></div>
</template>

<script>
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
    .setView([55.8642, -4.2518], 13)
    .addLayer(this.osmLayer);

    this.murals.forEach((mural, index) => {
        L.marker(mural.coords)
        .addTo(this.map)
        .on('click', () => {
          console.log(index);
        })
  })
  }
}
</script>

<style lang="css" scoped>
#mapContainer{
  width:500px;
  height:500px;
}
</style>
