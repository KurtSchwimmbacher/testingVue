<script setup>
import { ref, onMounted } from 'vue';
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
// import { ScrollSmoother } from 'gsap/ScrollSmoother';
import '@splinetool/viewer';


import Hero from './components/Hero.vue';
import NavigationBar from './components/NavigationBar.vue';


</script>

<template>
  <div>
    <NavigationBar />
    <Hero />
    

    <div  ref="spline" class="spline">
      <spline-viewer url="https://prod.spline.design/7a9DMp8cKTGnbXCs/scene.splinecode"></spline-viewer>
    </div>


  </div>


   
</template>

<style>

html, body {
  scroll-behavior: smooth;
}

.spline{
  z-index: -5;
  position: absolute;
  top: 0;
}

</style>
