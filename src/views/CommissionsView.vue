<script setup>
import { ref } from 'vue'

const hover = ref(false)
</script>

<template>
  <div class="commissions">
    <h1>Commissions</h1>
    <h3>I am open for commissions.</h3>
    <h3>I use Kofi for commissions, click on the image below to go to my page.</h3>
    <p>(For now, ask for prices in DMs please)</p>
    <!-- open in new tab -->
    <a href="https://ko-fi.com/vlashikito/commissions" target="_blank" rel="noopener noreferrer">
      <img
        @mouseenter="hover = true"
        @mouseleave="hover = false"
        :src="hover ? '/commissions/buy.jpg' : '/commissions/kofi.png'"
        alt="I'm not sorry"
      />
    </a>
  </div>
</template>

<style scoped>
h3 {
  margin-top: 0.5rem;
  line-height: 1.2;
  max-width: 350px;
  margin-left: 1rem;
  margin-right: 1rem;
}

h1 {
  margin-bottom: 0.5rem;
}

.commissions {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  max-width: 1000px;
  text-align: center;
}

.commissions img {
  max-height: 230px;
  max-width: 80vw;
  margin-top: 0.5rem;
  transition: transform 0.17s ease-out;
  cursor: pointer;
}

.commissions img:hover {
  transform: scale(1.05);
}
</style>
