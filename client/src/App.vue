<template lang="html">
  <div>
    <mapView :murals="murals"/>
  </div>
</template>

<script>
import MapView from "./components/MapView.vue";
import { eventBus } from './main.js';

export default {
  data(){
    return {
      selectedMural: null,
      murals: []
    }
  },
  components: {
    'mapView': MapView
  },
  mounted(){
      fetch("http://localhost:3000/api/murals")
      .then(response => response.json())
      .then(murals => this.murals = murals)

      eventBus.$on('marker-clicked', index => this.selectedMural = this.murals[index])
  }
}
</script>

<style lang="css" scoped>
</style>
