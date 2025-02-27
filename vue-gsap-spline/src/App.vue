<script setup>
import { ref, onMounted } from 'vue';
import { gsap } from 'gsap';
import '@splinetool/viewer';

const box = ref(null);

</script>

<template>
   <div class="hero">
    <spline-viewer url="https://prod.spline.design/TUufPLGVEZGWCiED/scene.splinecode"></spline-viewer>
  </div>
</template>

<style>
body {
  background-color: #A8B2B5; 
  color: #1f1f1f; 
}

.hero{
  border: 2px solid#1f1f1f;
  width: 100vw;
  height: 100vh;
  margin-left: -11% !important;
  margin-top: -3%;
  overflow: hidden !important;
}


</style>
