<template>
  <div id="art-section">
    <div class="content-container">
      <img
        src="/src/assets/images/illustration-phones.svg"
        alt="illustration"
        class="illustration"
      />
      <div class="text">
        <h2>State of the Art Infrastructure</h2>
        <p>
          With reliability and speed in mind, worldwide data centers provide the backbone for
          ultra-fast connectivity. This ensures your site will load instantly, no matter where your
          readers are, keeping your site competitive.
        </p>
      </div>
    </div>
  </div>
</template>

<script setup></script>

<style scoped>
#art-section {
  background-color: var(--color-text-headings);
  border-bottom-left-radius: 100px;
  border-top-right-radius: 100px;
  width:;
}

.content-container {
  max-width: 1110px;
  margin: 0 auto;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
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
  top: 0;
  height: 100%;
  width: auto;
  object-fit: cover;
  z-index: 1;
  overflow: hidden;
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
