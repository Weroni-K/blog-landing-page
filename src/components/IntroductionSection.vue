<template>
  <div id="find-out-section">
    <h2 class="title">Designed for the future</h2>
    <div class="content-container">
      <div class="text">
        <h3>Introducing an extensible editor</h3>
        <p>
          Blogr features an exceedingly intuitive interface which lets you focus on one thing:
          creating content. The editor supports management of multiple blogs and allows easy
          manipulation of embeds such as images, videos, and Markdown. Extensibility with plugins
          and themes provide easy ways to add functionality or change the looks of a blog.
        </p>
        <h3>Robust content management</h3>
        <p>
          Flexible content management enables users to easily move through posts. Increase the
          usability of your blog by adding customized categories, sections, format, or flow. With
          this functionality, you’re in full control.
        </p>
      </div>
      <img :src="editorImage" class="editor-illustration" alt="Editor Image" />
    </div>
  </div>
</template>

<script setup>
import { computed, reactive, onMounted, onBeforeUnmount } from 'vue'
import EditorImageDesktop from '../assets/images/illustration-editor-desktop.svg'
import EditorImageMobile from '../assets/images/illustration-editor-mobile.svg'
const editorImage = computed(() => {
  return isDesktop.value ? EditorImageDesktop : EditorImageMobile
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
  return windowSize.width >= 1180
})
</script>

<style scoped>
#find-out-section {
  max-width: 1110px;
  margin: 1rem auto;
  height: 55rem;
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
.editor-illustration {
  position: relative;
  right: 0;
  margin-right: -40%;
  top: 0;
  height: 100%;
  width: auto;
  object-fit: cover;
  z-index: 1;
  overflow: hidden;
}
.find-out-button {
  height: 100%;
  padding: 8px 2rem;
  color: var(--color-neutral-light-grey);
  background: transparent;
  border: 2px solid var(--color-neutral-light-grey);
  font-weight: var(--font-weight-700);
}

.find-out-button:hover {
  cursor: pointer;
  color: var(--color-neutral-very-dark-violet);
  background-color: var(--color-neutral-light-grey);
}

h2,
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

@media (max-width: 1180px) {
  #find-out-section {
    margin: 8rem 24px;
    padding: 3rem 4rem;
  }
  h2 {
    font-size: 48px;
  }
}

@media (max-width: 768px) {
  #find-out-section {
    margin-top: 5rem;
    padding: 4rem 1rem;
    flex-direction: column;
    text-align: center;
    gap: 3rem;
  }
  h2 {
    font-size: 40px;
  }
  .find-out-button {
    font-size: 14px;
  }
}
</style>
