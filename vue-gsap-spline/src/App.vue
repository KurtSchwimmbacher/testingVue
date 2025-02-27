<script setup>
import { ref, onMounted } from 'vue';
import { gsap } from 'gsap';
import '@splinetool/viewer';


// Navbar reference
const navbar = ref(null);

onMounted(() => {
  // Slide in the navbar from the top
  gsap.from(navbar.value, {
    y: -100, // Move from above the screen
    opacity: 0,
    duration: 2,
    ease: "power2.out"
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

    <div class="hero">
      <spline-viewer url="https://prod.spline.design/TUufPLGVEZGWCiED/scene.splinecode"></spline-viewer>
    </div>
  </div>
   
</template>

<style>
/* Set background color */
body {
  background-color: #A8B2B5; 
  color: #1f1f1f; 
  margin: 0; /* Prevent default margins */
  overflow: hidden; /* Stop scrollbars */
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
  width: 100vw;
  height: 100vh;
  margin-top: 3%;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

/* Make Spline viewer fill the section */
spline-viewer {
  width: 100%;
  height: 100%;
}


</style>
