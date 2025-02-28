<script setup>
import { ref, onMounted } from 'vue';
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import { ScrollSmoother } from 'gsap/ScrollSmoother';
import '@splinetool/viewer';

gsap.registerPlugin(ScrollTrigger, ScrollSmoother);

// Navbar reference
const navbar = ref(null);
const aboutSection = ref(null);
const smoothWrapper = ref(null);
const smoothContent = ref(null);

onMounted(() => {
  // Slide in the navbar from the top
  gsap.from(navbar.value, {
    y: -100, // Move from above the screen
    opacity: 0,
    duration: 2,
    ease: "power2.out"
  });

  gsap.from(".about-section", {
    opacity: 0,
    y: 50,
    duration: 1.5,
    scrollTrigger: {
      trigger: ".about-section",
      start: "top 80%", // Start animation when section is 80% in view
      toggleActions: "play none none reverse",
    }
  });

  // Scroll-triggered scale effect on experimental section
  gsap.from(".experiment-box", {
    scale: 0.8,
    opacity: 0,
    duration: 1.5,
    scrollTrigger: {
      trigger: ".experiment-section",
      start: "top 75%",
      toggleActions: "play none none reverse",
    }
  });


});


</script>

<template>
  <div>

    <!-- Navbar -->
    <nav ref="navbar" class="navbar">
      <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Projects</a></li>
        <li><a href="#">Contact</a></li>
      </ul>
    </nav>

    <div  ref="hero" class="hero">
      <spline-viewer url="https://prod.spline.design/TUufPLGVEZGWCiED/scene.splinecode"></spline-viewer>
    </div>

    <p class="scroll-down">Scroll Down for more</p>

  </div>

    <!-- About Section -->
    <section ref="aboutSection" class="about-section">
      <h2>About This Project</h2>
      <p>
        This is a test project using Vue and Spline. Scroll down to explore more content!
      </p>
    </section>

  
   
</template>

<style>

html, body {
  scroll-behavior: smooth;
}

body {
  background-color: #A8B2B5; 
  color: #1f1f1f; 
  margin: 0; /* Prevent default margins */
  overflow-x: hidden; /* Stop scrollbars */
}


/* Navbar Styles */
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  /* padding: 20px; */
  background: #A8B2B5;
  backdrop-filter: blur(10px); /* Frosted glass effect */
  display: flex;
  justify-content: center;
  z-index: 1000;
}

.navbar ul {
  display: flex;
  gap: 20px;
  list-style: none;
  padding: 0;
}

.navbar li {
  padding: 10px;
}

.navbar a {
  color: #f7f7f7;
  text-decoration: none;
  font-weight: bold;
  font-size: 18px;
  transition: color 0.3s;
}

.navbar a:hover {
  color: #EF6351;
}



/* Fullscreen Hero Section */
.hero {
  width: 100rem;
  height: 100vh;
  margin-top: 3%;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  margin-left: -15% !important;

  position: relative;
  z-index: 1;
  pointer-events: none; /* Prevent Spline from capturing scroll */
}

/* Make Spline viewer fill the section */
spline-viewer {
  pointer-events: auto; 
  width: 100%;
  height: 100%;
}

.scroll-down{
  position: relative;
  margin-top: -12%;
  z-index: 1000;
  margin-bottom: 12%;
}

/* About Section */
.about-section {
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  
  padding: 50px;
  text-align: center;
  
  border-radius: 25px !important;

  background: rgba(255, 255, 255, 0.2);
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(11.1px);
  -webkit-backdrop-filter: blur(11.1px);
  border: 1px solid rgba(255, 255, 255, 0.3);
}

.about-section h2 {
  font-size: 2rem;
  margin-bottom: 20px;
}

.about-section p {
  font-size: 1.2rem;
  max-width: 600px;
}


</style>
