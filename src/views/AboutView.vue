<script setup>
import anime from 'animejs/lib/anime.es.js'
import { ref } from 'vue'

const vlashikitoFace = ref(1)
const maxFaces = 5

function bounceAndSkip() {
  anime({
    targets: '.bounce-and-skip',
    scale: [
      { value: 0.8, duration: 70, easing: 'easeOutSine' },
      { value: 1.15, duration: 130, easing: 'easeInOutSine' },
      { value: 0.9, duration: 200, easing: 'easeInOutSine' },
      { value: 1, duration: 280, easing: 'easeInOutSine' }
    ],
    easing: 'easeOutQuad'
  })

  setTimeout(() => {
    let newVal = 1 + Math.floor(Math.random() * maxFaces)
    while (newVal === vlashikitoFace.value) {
      newVal = 1 + Math.floor(Math.random() * maxFaces)
    }
    vlashikitoFace.value = newVal
  }, 50)
}
</script>

<template>
  <div class="about">
    <h1>About Me</h1>
    <img
      :src="`/about/avatar${vlashikitoFace}.png`"
      alt="logo"
      class="bounce-and-skip"
      @click="bounceAndSkip"
    />
    <h3>I'm just a guy from France who wants to create great stories</h3>
  </div>
</template>

<style scoped>
img {
  margin-top: 2rem;
  margin-bottom: 1.5rem;
  width: 10rem;
  height: 10rem;
}

h3 {
  max-width: 300px;
  line-height: 1.2;
}

.about {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  max-width: 500px;
  text-align: center;
  margin-bottom: 2rem;
  margin-left: 1rem;
  margin-right: 1rem;
}
</style>
