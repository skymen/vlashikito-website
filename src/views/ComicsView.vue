<script setup>
import { ref } from 'vue'

const comics = [
  {
    name: 'Magical Girl Riot',
    thumbnail: '/comics/comic1.png',
    nameHover: 'Magical Girl Riot',
    thumbnailHover: '/comics/comic1.png',
    link: 'https://www.webtoonfactory.com/fr/serie/magical-girl-riot/'
  },
  {
    name: 'Isabelle',
    thumbnail: '/comics/comic2.png',
    nameHover: '- Oui ?',
    thumbnailHover: '/comics/comic2hover.png',
    link: 'https://www.webtoons.com/fr/canvas/isabelle/list?title_no=686563'
  }
]
const hover = ref(Array(comics.length).fill(false))
</script>

<template>
  <div class="comicsWrapper">
    <h1>Comics</h1>
    <div class="comics">
      <div v-for="(comic, i) in comics" :key="comic.name" class="comic">
        <!-- open in new tab -->
        <a :href="comic.link" target="_blank" rel="noopener noreferrer">
          <img
            :src="hover[i] ? comic.thumbnailHover : comic.thumbnail"
            :alt="hover[i] ? comic.nameHover : comic.name"
            @mouseover="hover[i] = true"
            @mouseleave="hover[i] = false"
          />
          <p>{{ hover[i] ? comic.nameHover : comic.name }}</p>
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped>
img {
  margin-top: 2rem;
  width: 10rem;
  height: 10rem;
}

.comicsWrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  max-width: 800px;
  text-align: center;
}

.comics {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}

.comic {
  margin: 1rem 2rem;
}

.comic p {
  margin-top: 0.5rem;
  font-size: 1.2rem;
  font-weight: bold;
  text-align: center;
  user-select: none;
}

.comic img {
  transition: transform 0.17s ease-out;
}

.comic:hover img {
  transform: scale(1.15);
}
</style>
