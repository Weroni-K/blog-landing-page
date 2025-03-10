<template>
  <div id="features-section">
    <div class="content-container">
      <img :src="laptopImage" class="laptop-illustration" alt="Laptop Image" />
      <div class="text">
        <h3>Free, open, simple</h3>
        <p>
          Blogr is a free and open source application backed by a large community of helpful
          developers. It supports features such as code syntax highlighting, RSS feeds, social media
          integration, third-party commenting tools, and works seamlessly with Google Analytics. The
          architecture is clean and is relatively easy to learn.
        </p>
        <h3>Powerful tooling</h3>
        <p>
          Batteries included. We built a simple and straightforward CLI tool that makes
          customization and deployment a breeze, but capable of producing even the most complicated
          sites.
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed, reactive, onMounted, onBeforeUnmount } from 'vue'
import LaptopImageDesktop from '../assets/images/illustration-laptop-desktop.svg'
import LaptopImageMobile from '../assets/images/illustration-laptop-mobile.svg'
const laptopImage = computed(() => {
  return isDesktop.value ? LaptopImageDesktop : LaptopImageMobile
})

const windowSize = reactive({
  width: window.innerWidth,
  height: window.innerHeight,
})

const updateWindowSize = () => {
  windowSize.width = window.innerWidth
  windowSize.height = window.innerHeight
}

onMounted(() => {
  window.addEventListener('resize', updateWindowSize)
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', updateWindowSize)
})

const isDesktop = computed(() => {
  return windowSize.width >= 768
})
</script>

<style scoped>
#features-section {
  max-width: 1110px;
  margin: 6rem auto auto;
  height: 56rem;
}

.content-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.title {
  position: relative;
  text-align: center;
  top: 8rem;
}

.text {
  display: flex;
  flex-direction: column;
  max-width: 50%;
  gap: 1rem;
}

.laptop-illustration {
  position: relative;
  left: 0;
  margin-left: -40%;
  top: 0;
  height: 100%;
  width: auto;
  object-fit: cover;
  z-index: 1;
  overflow: hidden;
}

h3 {
  color: var(--color-text-headings);
}

p {
  color: var(--color-text-body-copy);
  padding-bottom: 3.5rem;
}

p:last-child {
  padding-bottom: 0;
}

.features-title {
  padding: 4rem 0;
}

.features-cards {
  columns: 3;
  padding: 2rem 0;
  gap: 2rem;
}

@media (max-width: 1180px) {
  #features-section {
    margin: 5rem 0;
    height: auto;
  }
  h2 {
    font-size: 46px;
  }
}

@media (max-width: 768px) {
  #features-section {
    margin-top: 2rem;
  }
  .content-container {
    flex-direction: column;
  }
  .laptop-illustration {
    position: relative;
    left: 0;
    top: 0;
    height: 100%;
    aspect-ratio: 1;
    z-index: 1;
    overflow: hidden;
    margin: 2rem 0;
  }
  .text {
    text-align: center;
    max-width: 100%;
    margin-inline: 24px;
  }
  p {
    letter-spacing: 0.2px;
    word-spacing: 0.5px;
  }
  .features-cards {
    padding: 0;
    display: flex;
    flex-direction: column;
    gap: 3.5rem;
  }
  .features-title {
    padding-top: 3rem;
  }
}
</style>
