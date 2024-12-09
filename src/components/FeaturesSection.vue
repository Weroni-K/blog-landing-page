<template>
  <div id="features-section">
    <div class="content-container">
      <img
        src="/src/assets/images/illustration-laptop-desktop.svg"
        alt="illustration"
        class="illustration"
      />
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

<script setup></script>

<style scoped>
#features-section {
  max-width: 1110px;

  margin: auto;
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
.illustration {
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
    margin: 0 24px;
  }
  h2 {
    font-size: 46px;
  }
}

@media (max-width: 768px) {
  h2 {
    text-align: center;
  }
  .features-cards {
    padding: 1.5rem 0;
    display: flex;
    flex-direction: column;
    gap: 3.5rem;
  }
  .features-card {
    justify-items: center;
    text-align: center;
  }
  .features-title {
    padding-top: 3rem;
  }
}
</style>
