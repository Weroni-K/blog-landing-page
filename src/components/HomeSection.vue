<template>
  <div id="home-section">
    <div class="content-container">
      <h1>A modern publishing platform</h1>
      <p>Grow your audience and build your online brand</p>
      <a href="./">
        <button class="start-free-button">Start for Free</button>
        <button class="learn-more-button">Learn More</button>
      </a>
    </div>
  </div>
</template>

<script setup>
import { computed, reactive, onMounted, onBeforeUnmount } from 'vue'

// const introImage = computed(() => {
//   return isDesktop.value ? IntroImageDesktop : IntroImageMobile
// })

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
  return windowSize.width >= 1180
})
</script>
<style scoped>
#home-section {
  position: relative;
  padding: 0;
  padding-top: 5rem;
  margin: 0 auto;
  z-index: 2;
}

.content-container {
  max-width: 1110px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  gap: 0;
}

h1 {
  overflow-wrap: break-word;
}

p {
  font-size: 20px;
  padding-bottom: 2.4rem;
}

.start-free-button {
  height: 3rem;
  width: 8.75rem;
  padding: 8px 0;
  color: var(--color-text-cta);
  border: none;
  border-radius: 1.5rem;
  font-weight: var(--font-weight-700);
  margin-right: 1rem;
}

.start-free-button:hover {
  cursor: pointer;
  color: var(--color-text-body-white);
  background-color: var(--color-bg-cta-hover);
}

.learn-more-button {
  height: 3rem;
  width: 8.75rem;
  padding: 8px 0;
  background: transparent;
  border: 1px solid var(--color-text-body-white);
  border-radius: 1.5rem;
  font-weight: var(--font-weight-700);
}

.learn-more-button:hover {
  cursor: pointer;
  color: var(--color-bg-cta-hover);
  background-color: var(--color-text-body-white);
}

@media (max-width: 1180px) {
  #home-section {
    padding-inline: 24px;
  }
}
@media (max-width: 768px) {
  .content-container {
    text-align: center;
    font-weight: var(--font-weight-400);
  }
  h1 {
    font-size: 34px;
    line-height: 1.25;
    padding-bottom: 0.5rem;
  }
  p {
    font-size: 18px;
  }
}
</style>
