<script setup>
import Gallery from '../components/Gallery.vue'
import images from '../assets/images.json'
</script>

<template>
  <div class="gallery">
    <h1>Gallery</h1>
    <Gallery id="commissions" :items="images"></Gallery>
  </div>
</template>

<style scoped>
h3 {
  margin-bottom: 1rem;
  margin-top: 1rem;
  line-height: 1.2;
  max-width: 350px;
  margin-left: 1rem;
  margin-right: 1rem;
}

.gallery {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  max-width: 1000px;
  text-align: center;
}
</style>
