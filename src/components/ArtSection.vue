<template>
  <div id="art-section">
    <div class="content-container">
      <div class="picture">
        <img
          src="/src/assets/images/illustration-phones.svg"
          alt="illustration"
          class="illustration"
        />
      </div>
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
  background: var(--color-bg-gradient-body);
  border-bottom-left-radius: 100px;
  border-top-right-radius: 100px;
  width: 100%;
  position: relative;
  height: 25rem;
  background-repeat: no-repeat;
  background-position: bottom;
  display: flex;
}

.content-container {
  max-width: 1110px;
  margin: 0 auto 0;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  gap: 4rem;
  align-items: center;
  max-height: 100%;
}

.content-container::before {
  content: '';
  position: absolute;
  top: -120%;
  left: -15%;
  width: 100%;
  height: 255%;
  background: url('./src/assets/bg/bg-pattern-circles.svg') no-repeat bottom left;
  background-size: contain;
  z-index: 0;
  clip-path: inset(47% 0 14% 10%);
}

.text {
  display: flex;
  flex-direction: column;
  width: 50%;
  gap: 1rem;
  padding: 4rem 0;
  z-index: 1;
}

.picture {
  width: 50%;
  object-fit: cover;
}

.illustration {
  position: relative;
  height: 200%;
  aspect-ratio: 1;
  z-index: 1;
}

p {
  letter-spacing: 0.6px;
  word-spacing: 0.4px;
}

@media (max-width: 1180px) {
  #art-section {
    height: auto;
  }
  .content-container {
    margin-inline: 24px;
  }
  h2 {
    font-size: 46px;
  }
}

@media (max-width: 768px) {
  .content-container {
    margin-inline: 0px;
    flex-direction: column;
    gap: 1rem;
    max-height: none;
    height: 100%;
  }
  .content-container::before {
    top: -35%;
    left: 0;
    width: 100%;
    height: 150%;
    background: url('./src/assets/bg/bg-pattern-circles.svg') no-repeat top center;
    background-size: cover;
    z-index: 0;
    clip-path: inset(24% 0 0 0);
  }
  .picture {
    width: 100%;
    max-width: 25rem;
  }
  .illustration {
    height: 100%;
    aspect-ratio: 1;
    margin-top: -50%;
  }
  .text {
    width: 100%;
    margin-bottom: 7rem;
    text-align: center;
    padding: 0 24px;
  }
  h2 {
    font-size: 36px;
    line-height: 1.4;
  }
  p {
    letter-spacing: 0.2px;
  }
}
</style>
