<script setup>
import { ref, onMounted } from "vue";
import gsap from "gsap";

const shortText = ref(null);
const fullText = ref(null);

onMounted(() => {
    // Initially hide full text
    gsap.set(fullText.value, { opacity: 0, y: 10 }); //start off screen - right 

    // Hover animation
    const navItem = document.querySelector(".nav-item a");

    navItem.addEventListener("mouseenter", () => {
        gsap.to(shortText.value, { opacity: 0, y: -10, duration: 0.4, ease: "power2.out" });
        gsap.to(fullText.value, { opacity: 1, y: 0, duration: 0.4, ease: "power2.out" });
    });

    navItem.addEventListener("mouseleave", () => {
        gsap.to(shortText.value, { opacity: 1, y: 0, duration: 0.4, delay: 0.2, ease: "power2.inOut" });
        gsap.to(fullText.value, { opacity: 0, y: 10, duration: 0.4, delay:0.2, ease: "power2.inOut" });
    });
});
</script>

<template>
    <nav class="navbar">
        <ul class="nav-list">
            <li class="nav-item">
                <a href="#">
                    <span ref="shortText" class="short">K <br> <strong class="S" >S</strong></span>
                    <span ref="fullText" class="full">Kurt <br> <strong class="S" >Schwimmbacher</strong></span>
                </a>
            </li>
        </ul>
    </nav>
</template>

<style scoped>

.S {
    margin-left: 0.5rem;
}

.nav-list {
    list-style: none;
    display: flex;
    justify-content: left;
    margin: 0;
    padding: 0;
}

.nav-item a {
    color: white;
    text-decoration: none;
    font-size: 1.3rem;
    display: flex;
    flex-direction: column;
    position: relative;
    /* overflow: hidden; */
}

.short,
.full {
    position: absolute;
    left: 0;
    right: 0;
    text-align: left;
}
</style>
