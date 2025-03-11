<script setup>
import { ref, onMounted } from "vue";
import { gsap } from "gsap";

const letters = ref([]); // Store multiple letter elements

onMounted(() => {
  function animateLetters() {
    if (!letters.value.length) return; // Ensure elements exist

    const selectedLetters = letters.value.filter(() => Math.random() < 0.5); // Randomly select ~50% of letters

    selectedLetters.forEach((letter) => {
      const flipDirection = Math.random() > 0.5 ? "rotateX" : "rotateY"; // Random X/Y flip

      gsap.fromTo(
        letter,
        { [flipDirection]: "180deg", opacity: 0 },
        {
          [flipDirection]: "0deg",
          opacity: 1,
          duration: 0.8,
          ease: "none",
        }
      );
    });
  }

  // Initial animation
  animateLetters();

  // Repeat animation every 5 seconds
  setInterval(animateLetters, 5000);
});
</script>

<template>
  <section class="hero">
    <div class="hero-content">
      <div class="big-text">
        <span
          v-for="(letter, index) in 'Bridging UX Code & Interactive Worlds'"
          :key="index"
          ref="letters"
          class="letter"
        >
          {{ letter }}
        </span>
      </div>
      <div class="arrow">↓</div>
    </div>
  </section>
</template>

<style scoped>
@font-face {
  font-family: "Outward-block";
  src: url("/src/assets/fonts/outward-block-webfont.woff2") format("woff2");
  font-weight: normal;
  font-style: normal;
}

.hero {
    z-index: 1000;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  height: 100vh;
  font-family: "Outward-block", sans-serif;
}

.big-text {
  font-size: 14rem;
  letter-spacing: 0.1em;
  color: #e5e5e5;
}

.letter {
  display: inline-block;
  transform-origin: center;
}
</style>
