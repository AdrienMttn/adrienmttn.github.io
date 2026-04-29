<script setup lang="ts">
import { onMounted } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import HeaderComponent from "./components/header.vue";
import SocialMedia from "./components/SocialMedia.vue";
import Contact from "./vue/contact.vue";
import Home from "./vue/home.vue";
import Parcours from "./vue/parcours.vue";
import Project from "./vue/project.vue";


gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
    gsap.to('#socialMediaSection', {
      scrollTrigger: {
        trigger: "#contactSection",
        start: 'top center',
        end: 'bottom center',
        onEnter: () => {
          gsap.to('#socialMediaSection', { x: 100, duration: 0.5 });
        },
        onLeave: () => {
          gsap.to('#socialMediaSection', { x: 0, duration: 0.5 });
        },
        onEnterBack: () => {
          gsap.to('#socialMediaSection', { x: 100, duration: 0.5 });
        },
        onLeaveBack: () => {
          gsap.to('#socialMediaSection', { x: 0, duration: 0.5 });
        },
        scrub: true,
      }
    });
});
</script>

<template>
  <HeaderComponent />
  <SocialMedia/>
  <Home />
  <Parcours />
  <Project/>
  <Contact/>
</template>

<style scoped></style>
