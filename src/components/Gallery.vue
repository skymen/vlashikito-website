<script setup>
import PhotoSwipeLightbox from 'photoswipe/lightbox'
import 'photoswipe/style.css'
import { ref, onMounted, onUnmounted } from 'vue'

const props = defineProps({
  items: {
    type: Array,
    required: true
  },
  id: {
    type: String,
    required: true
  }
})

const lightbox = ref(null)

onMounted(() => {
  lightbox.value = new PhotoSwipeLightbox({
    gallery: `#${props.id}`,
    children: 'a',
    pswpModule: () => import('photoswipe')
  })
  lightbox.value.init()
})

onUnmounted(() => {
  lightbox.value.destroy()
  lightbox.value = null
})
</script>

<template>
  <div :id="props.id" class="images">
    <div
      :class="`image ${image.width / image.height > 1 ? 'imageLandscape' : 'imagePortrait'}`"
      v-for="(image, key) in props.items"
      :style="`aspect-ratio:${image.width / image.height}`"
    >
      <a
        :key="key"
        :href="image.largeURL"
        :data-pswp-width="image.width"
        :data-pswp-height="image.height"
        target="_blank"
        rel="noreferrer"
      >
        <img :src="image.thumbnailURL" alt="" />
      </a>
    </div>
  </div>
</template>

<style scoped>
.images {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  max-width: 1000px;
  margin: 0 auto;
}
.image {
  display: flex;
  justify-content: center;
  align-items: center;
  /* width: 150px;
  height: 150px; */
  border: 2px solid var(--color-main);
  border-radius:;
  margin: 0.5rem;
  cursor: pointer;
}

.imagePortrait {
  max-width: 150px;
}
.imageLandscape {
  max-height: 150px;
}

.image a {
  line-height: 0;
  padding: 0.2rem;
  margin: 0;
}

.image img {
  width: 100%;
  height: 100%;
}
</style>
