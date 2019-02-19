<template lang="html">
  <img v-if="imageSrc" :src="imageSrc"/>
</template>

<script>
export default {
  name: 'muralImage',
  props: ['imgTag'],
  data(){
    return {
      imageSrc: null
    }
  },
  mounted(){
    fetch(`https://api.flickr.com/services/rest/?&method=flickr.photos.search&api_key=e83c635ab5aca5ad0990f1d779a36309&text=${this.imgTag}&format=json&nojsoncallback=1`)
    .then(response => response.json())
    .then(data => {
      const photo = data.photos.photo[0];
      const url = `https://farm${photo.farm}.staticflickr.com/${photo.server}/${photo.id}_${photo.secret}.jpg`;
      this.imageSrc = url;
     })
   },
   watch: {
     imgTag: function(imgTag){
       fetch(`https://api.flickr.com/services/rest/?&method=flickr.photos.search&api_key=e83c635ab5aca5ad0990f1d779a36309&text=${imgTag}&format=json&nojsoncallback=1`)
       .then(response => response.json())
       .then(data => {
         const photo = data.photos.photo[0];
         const url = `https://farm${photo.farm}.staticflickr.com/${photo.server}/${photo.id}_${photo.secret}.jpg`;
         this.imageSrc = url;
        })
     }
   }
  }
</script>

<style lang="css" scoped>
</style>
