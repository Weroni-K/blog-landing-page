<template>
  <div id="header-section">
    <div class="navbar">
      <div class="logo">
        <img src="/src/assets/logo.svg" alt="Insure logo" class="insure-logo" />
      </div>

      <div class="nav-links" :class="{ active: isMenuOpen }" v-if="windowWidth > 768 || isMenuOpen">
        <div class="nav-menu">
          <div
            v-for="(link, index) in menuLinks"
            :key="index"
            class="nav-link"
            @mouseover="toggleSubMenu(index, true)"
            @mouseleave="toggleSubMenu(index, false)"
          >
            <a
              :href="link.url"
              class="menu-link"
              @mouseover="link.showSubMenu = true"
              @mouseleave="link.showSubMenu = false"
              ><p>
                {{ link.text }}
              </p>
              <img
                src="/src/assets/icons/icon-arrow-light.svg"
                alt="Dropdown arrow"
                class="arrow-icon"
                :class="{ rotate: link.showSubMenu }"
              />
              <ul v-if="link.showSubMenu" class="submenu">
                <li v-for="(subLink, i) in link.submenu" :key="i">
                  <a :href="subLink.url" class="submenu-link">{{ subLink.text }}</a>
                </li>
              </ul>
            </a>
          </div>
        </div>
        <div class="nav-buttons">
          <button class="login-button">Login</button>
          <button class="start-free-button">Sign Up</button>
        </div>
      </div>

      <button
        class="burger"
        @click="toggleMenu"
        aria-label="Toggle menu"
        v-if="windowWidth <= 768"
        :class="{ active: isMenuOpen }"
      >
        <span class="line-top"></span>
        <span class="line-mid"></span>
        <span class="line-bottom"></span>
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const menuLinks = ref([
  {
    text: 'Product',
    url: './',
    showSubMenu: false,
    submenu: [
      { text: 'Overview', url: './overview' },
      { text: 'Pricing', url: './pricing' },
      { text: 'Marketplace', url: './marketplace' },
      { text: 'Features', url: './features' },
      { text: 'Integrations', url: './integrations' },
    ],
  },
  {
    text: 'Company',
    url: './',
    showSubMenu: false,
    submenu: [
      { text: 'About', url: './about' },
      { text: 'Team', url: './team' },
      { text: 'Blog', url: './blog' },
      { text: 'Careers', url: './careers' },
    ],
  },
  {
    text: 'Connect',
    url: './',
    showSubMenu: false,
    submenu: [
      { text: 'Contact', url: './contact' },
      { text: 'Newsletter', url: './newsletter' },
      { text: 'LinkedIn', url: './linkedin' },
    ],
  },
])

const isMenuOpen = ref(false)
const windowWidth = ref(window.innerWidth)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
  document.body.style.overflow = isMenuOpen.value ? 'hidden' : ''
}

const toggleSubMenu = (index, status) => {
  menuLinks.value[index].showSubMenu = status
}

const handleResize = () => {
  windowWidth.value = window.innerWidth
  if (windowWidth.value > 768) {
    isMenuOpen.value = false
  }
}

onMounted(() => {
  window.addEventListener('resize', handleResize)
})

onUnmounted(() => {
  window.removeEventListener('resize', handleResize)
})
</script>

<style scoped>
#header-section {
  max-width: 1110px;
  margin: 0 auto;
  padding: 3rem 0;
  z-index: 2;
}

.navbar {
  height: 4rem;
  display: flex;
  align-items: center;
  gap: 4rem;
}

.no-scroll {
  overflow: hidden;
}
.logo img {
  width: 7rem;
}
.nav-links {
  margin: 0;
  padding: 0;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 2rem;
  color: var(--color-neutral-dark-greyish-violet);

  z-index: 2;
  p {
    font-size: 16px;
    font-weight: var(--font-weight-700);
  }
  p:hover {
    color: var(--color-neutral-very-dark-violet);
    text-decoration: underline;
  }
}

.nav-link {
  position: relative;
  cursor: pointer;
  display: ruby;
}

.arrow-icon {
  margin-left: 0.25rem;
  width: 12px;
  height: 8px;
  transition: transform 0.3s ease;
  vertical-align: middle;
}

.rotate {
  transform: rotate(180deg);
}

.submenu {
  position: absolute;
  top: 2.5rem;
  left: -1.5rem;
  width: 10rem;
  height: auto;
  display: none;
  background-color: var(--color-text-body-white);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  padding: 1rem 1.5rem;
  border-radius: 0.25rem;
  z-index: 20;
  color: var(--color-bg-footer);
}

.menu-link:hover .submenu {
  display: block;
}

.submenu li {
  margin: 0.25rem 0;
}

.submenu-link {
  text-decoration: none;
  font-size: 14px;
  font-weight: var(--font-weight-500);
  font-family: var(--font-headings);
}

.submenu-link:hover {
  font-weight: var(--font-weight-700);
}

.nav-menu {
  display: flex;
  gap: 2rem;
}

.nav-buttons {
  display: flex;
  gap: 2rem;
}

.login-button {
  height: 2rem;
  width: auto;
  padding: 8px 0;
  background: transparent;
  border: none;
  font-weight: var(--font-weight-700);
}

.login-button:hover {
  cursor: pointer;
  color: var(--color-text-cta);
}

.start-free-button {
  height: 3rem;
  width: 8.75rem;
  padding: 8px 0;
  color: var(--color-text-cta);
  border: none;
  border-radius: 1.5rem;
  font-weight: var(--font-weight-700);
}

.start-free-button:hover {
  cursor: pointer;
  color: var(--color-text-body-white);
  background-color: var(--color-bg-cta-hover);
}

.burger {
  padding: 8px 0px;
  width: 34px;
  height: 34px;
  display: none;
  flex-direction: column;
  border: none;
  background: transparent;
  cursor: pointer;
  z-index: 10;
  span {
    width: 30px;
    height: 2px;
    margin: auto;
    background: var(--color-text-body-white);
    transition: all 0.4s ease;
  }

  .line-top {
    transform: translateY(-2px);
  }

  .line-bottom {
    transform: translateY(2px);
  }

  &.active {
    .line-top {
      transform: translateY(8px) rotate(45deg);
    }
    .line-mid {
      transform: translateX(-6px) rotate(360deg);
      opacity: 0;
    }
    .line-bottom {
      transform: translateY(-4px) rotate(-45deg);
    }
  }
}
@media (max-width: 1175px) {
  #header-section {
    margin-inline: 24px;
  }
}
@media (max-width: 768px) {
  #header-section {
    padding: 1rem 0.5rem;
  }
  .navbar {
    height: 6rem;
  }
  .nav-links {
    margin: 0;
    width: 100%;
    height: 100vh;
    display: none;
    left: 0;
    top: 5rem;
    color: var(--color-neutral-light-grey);
    font-weight: var(--font-weight-400);
    font-size: 20px;
    a:hover {
      color: var(--color-neutral-dark-greyish-violet);
    }
  }

  .nav-links.active {
    position: absolute;
    top: 6rem;
    margin: 24px;
    width: calc(100% - 48px);
    height: calc(100vh - 8rem - 24px);
    display: flex;
    flex-direction: column;
    gap: 2rem;
    z-index: 10;
    padding: 2rem;
    color: var(--color-text-headings);
    background-color: var(--color-text-body-white);
    border-radius: 6px;
    box-shadow:
      rgba(255, 255, 255, 0.1) 0px 1px 1px 0px inset,
      rgba(50, 50, 93, 0.25) 0px 50px 100px -20px,
      rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;
  }
  .nav-menu {
    flex-direction: column;
  }
  .nav-buttons {
    flex-direction: column;
  }
  .view-plans-button {
    width: calc(100% - 48px);
    color: var(--color-neutral-light-grey);
    border: 2px solid var(--color-neutral-light-grey);
    font-weight: var(--font-weight-400);
  }

  .view-plans-button:hover {
    color: var(--color-neutral-very-dark-violet);
    background-color: var(--color-neutral-light-grey);
  }

  .burger {
    display: flex;
    position: absolute;
    right: 24px;
  }
}

@media (max-width: 768px) {
  #header-section {
    padding-inline: 24px;
  }
  .logo img {
    width: 5rem;
  }
}
</style>
