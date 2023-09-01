<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { ref } from 'vue'
import IconInstagram from './components/icons/IconInstagram.vue'
import IconTiktok from './components/icons/IconTiktok.vue'
import IconTwitter from './components/icons/IconTwitter.vue'

const titleFont = ref(0)
const vlashikitoFace = ref(1)
const maxFaces = 5
const fonts = [
  'AbrilFatface',
  'AmaticSC',
  'Bungee',
  'CarterOne',
  'LilitaOne',
  'Rowdies',
  // 'RubikIso',
  'UnicaOne',
  'Vlashikito'
]

setInterval(() => {
  titleFont.value = (titleFont.value + 1) % fonts.length

  if (fonts[titleFont.value] === 'Vlashikito') {
    vlashikitoFace.value = 1 + Math.floor(Math.random() * maxFaces)
  }
}, 370)

const socialIcons = [
  {
    name: 'twitter',
    link: 'https://twitter.com/vlashikito',
    icon: IconTwitter
  },
  {
    name: 'instagram',
    link: 'https://instagram.com/vlashikito',
    icon: IconInstagram
  },
  {
    name: 'tiktok',
    link: 'https://tiktok.com/@vlashikito',
    icon: IconTiktok
  }
]

const buttons = [
  {
    name: 'Commissions',
    to: '/commissions'
  },
  {
    name: 'Comics',
    to: '/comics'
  },
  {
    name: 'Gallery',
    to: '/gallery'
  },
  {
    name: 'About Me',
    to: '/about'
  }
]
</script>

<template>
  <main>
    <div class="title">
      <h1 :class="'title title' + titleFont" v-if="fonts[titleFont] !== 'Vlashikito'">
        <router-link to="/">VLASHIKITO</router-link>
      </h1>
      <div v-else class="avatar">
        <img :src="'/about/avatar' + vlashikitoFace + '.png'" alt="logo" />
      </div>
    </div>
    <h2>Manga x Webtoon creator</h2>
    <div class="social-icons">
      <a
        v-for="socialIcon in socialIcons"
        :key="socialIcon.name"
        :href="socialIcon.link"
        target="_blank"
        rel="noopener noreferrer"
      >
        <component :is="socialIcon.icon" />
      </a>
    </div>
    <div class="buttons">
      <router-link v-for="button in buttons" :key="button.name" :to="button.to" class="button">
        {{ button.name }}
      </router-link>
    </div>

    <footer>
      website by
      <a href="https://twitter.com/skymen75" target="_blank" rel="noopener noreferrer">skymen</a>
    </footer>
    <div class="content">
      <router-view v-slot="{ Component }">
        <transition name="slide-y" mode="out-in">
          <component :is="Component" />
        </transition>
      </router-view>
    </div>
  </main>
</template>

<style scoped>
h1 {
  cursor: pointer;
  user-select: none;
}

footer {
  width: calc(100% - 0.2rem);
  text-align: end;
  right: 0;
  bottom: 0;
  color: var(--color-white);
  opacity: 0.4;
  font-size: 0.7rem;
  margin-top: 1rem;
  margin-bottom: -1.2rem;
  margin-right: 1rem;
}

.title {
  height: 16vw;
}

.avatar {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}
.avatar img {
  width: 8vw;
  height: 8vw;
}

.social-icons {
  display: flex;
  justify-content: center;
  margin-top: 0.5rem;
  flex-wrap: wrap;
}

.social-icons a {
  display: inline-block;
  margin: 0 1rem;
}

.social-icons svg {
  width: 3rem;
  height: 3rem;
  fill: white;
  transition: fill 0.2s ease-in-out;
}

.social-icons svg:hover {
  fill: var(--color-main);
}

.buttons {
  display: flex;
  justify-content: center;
  margin-top: 1rem;
  flex-wrap: wrap;
}

.buttons .button {
  margin: 0.5rem 0.8rem;
  min-width: 10rem;
  text-align: center;
  padding: 0.5rem 1rem;
  border: 2px solid var(--color-main);
  border-radius: 0.5rem;
  color: var(--color-black);
  font-size: 1.2rem;
  font-weight: bold;
  text-decoration: none;
  transition: background-color 0.17s ease-in-out;
  background-color: var(--color-main);
}

@media (hover) {
  .buttons .button:hover {
    background-color: var(--color-black);
    /* background-color: rgb(142 211 57); */
    /* border-color: rgb(142 211 57); */
    color: var(--color-white);
    color: var(--color-main);
  }

  .buttons .router-link-active:hover {
    background-color: transparent;
    cursor: default;
    color: var(--color-main);
    border-color: var(--color-main);
  }
}

.buttons .router-link-active {
  background-color: transparent;
  color: var(--color-main);
}

.content {
  border-top: 1px solid rgba(var(--color-main-c), 0.4);
  display: flex;
  justify-content: center;
  align-items: center;
  padding-top: 0.8rem;
  margin-top: 1.4rem;
}
</style>
