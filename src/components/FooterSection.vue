<template>
  <div id="footer-section">
    <div class="footer-content">
      <div class="links-container">
        <div class="logo">
          <img src="/src/assets/logo.svg" alt="Blogr logo" class="blogr-logo" />
        </div>
        <div v-for="(column, titleIndex) in footerColumns" :key="titleIndex" class="links-column">
          <h4>{{ column.title }}</h4>
          <ul>
            <li v-for="(link, linkIndex) in column.links" :key="linkIndex">
              <a :href="link.url"
                ><p>{{ link.text }}</p></a
              >
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const footerColumns = ref([
  {
    title: 'Product',
    links: [
      { text: 'Overview', url: './' },
      { text: 'Pricing', url: './' },
      { text: 'Marketplace', url: './' },
      { text: 'Features', url: './' },
      { text: 'Integrations', url: './' },
    ],
  },
  {
    title: 'Company',
    links: [
      { text: 'About', url: './' },
      { text: 'Team', url: './' },
      { text: 'Blog', url: './' },
      { text: 'Careers', url: './' },
    ],
  },
  {
    title: 'Connect',
    links: [
      { text: 'Contact', url: './' },
      { text: 'Newsletter', url: './' },
      { text: 'LinkedIn', url: './' },
    ],
  },
])
</script>

<style scoped>
#footer-section {
  color: var(--color-text-footer);
  background-color: var(--color-bg-footer);
  border-top-right-radius: 6rem;
}

.footer-content {
  max-width: 1110px;
  margin: 0 auto;
  padding: 4.5rem 0 3.5rem;
}

.links-container {
  margin: auto;
  width: 100%;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.links-column,
.logo {
  flex: 1;
}

h4 {
  padding-bottom: 1.75rem;
}

p {
  color: var(--color-primary-dark-violet);
  font-weight: var(--font-weight-400);
  font-size: 15px;
  padding-bottom: 0.5rem;
}

p:hover {
  text-decoration: underline;
}

@media (max-width: 1180px) {
  .footer-content {
    margin: 0 24px;
  }
}

@media (max-width: 560px) {
  .links-container {
    flex-direction: column;
    align-items: center;
    gap: 2rem;
    text-align: center;
  }
  .logo {
    margin-bottom: 2.5rem;
  }
  h4 {
    font-size: 18px;
    padding-bottom: 1rem;
  }
  p {
    font-size: 18px;
    font-weight: var(--font-weight-500);
    line-height: 1.2;
  }
}
</style>
