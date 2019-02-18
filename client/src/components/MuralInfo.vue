<template lang="html">
    <div v-if="mural">
      <h1>{{mural.title}}</h1>
      <h2>{{mural.artist}}</h2>
      <muralImage :imgTag="mural.imageTags"/>
    </div>
</template>

<script>
import MuralImage from './MuralImage.vue';

export default {
  name: 'muralInfo',
  props: ['mural'],
  components: {
    'muralImage': MuralImage
  }
}
</script>

<style lang="css" scoped>
</style>
