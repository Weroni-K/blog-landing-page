<template>
  <div id="background-intro">
    <HeaderSection />
    <HomeSection />
  </div>
  <div id="background-body">
    <IntroductionSection />
    <ArtSection />
    <FeaturesSection />
  </div>
  <FooterSection />
</template>

<script setup>
import HeaderSection from './components/HeaderSection.vue'
import HomeSection from './components/HomeSection.vue'
import IntroductionSection from './components/IntroductionSection.vue'
import ArtSection from './components/ArtSection.vue'
import FeaturesSection from './components/FeaturesSection.vue'
import FooterSection from './components/FooterSection.vue'
</script>

<style scoped>
#background-intro {
  height: 37.5rem;
  width: 100%;
  margin: 0;
  padding: 0;
  border-bottom-left-radius: 6rem;
  background: var(--color-bg-gradient-intro);
  position: relative;
}

#background-intro::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: url('./assets/bg/bg-pattern-intro-desktop.svg') no-repeat left center;
  background-size: 220% auto;
  background-position: 25%;
}

#background-body {
  height: 100%;
  width: 100%;
  margin: 0;
  padding: 0;
  background-color: var(--color-text-body-white);
}

@media (max-width: 768px) {
  #background-intro {
    height: 37.5rem;
  }
}
</style>
