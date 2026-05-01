<script setup lang="ts">
import { onMounted } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import { ScrollSmoother } from 'gsap/ScrollSmoother';
import HeaderComponent from "./components/header.vue";
import SocialMedia from "./components/SocialMedia.vue";
import Contact from "./vue/contact.vue";
import Home from "./vue/home.vue";
import Parcours from "./vue/parcours.vue";
import Project from "./vue/project.vue";


gsap.registerPlugin(ScrollTrigger, ScrollSmoother);

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

    ScrollSmoother.create({
      smooth: 1, // how long (in seconds) it takes to "catch up" to the native scroll position
      effects: true, // looks for data-speed and data-lag attributes on elements
      smoothTouch: 0.1 // much shorter smoothing time on touch devices (default is NO smoothing on touch devices)
    });

    gsap.set(".flair", {xPercent: -50, yPercent: -50});

    let xTo = gsap.quickTo(".flair", "x", {duration: 0.2}),
    yTo = gsap.quickTo(".flair", "y", {duration: 0.2});
    window.addEventListener("mousemove", e => {
      xTo(e.clientX);
      yTo(e.clientY);
    });
});
</script>

<template>
  <div class="flair">
    <svg width="32" height="40" viewBox="0 0 14 18" fill="none">
      <path d="M0.5 0.5L13 10.5H5.5L2.5 17.5L0.5 0.5Z" stroke-width="0.5"></path>
    </svg>
  </div>
  <HeaderComponent />
  <SocialMedia/>
  <div id="smooth-wrapper">
    <div id="smooth-content">
      <Home />
      <Parcours />
      <Project/>
      <Contact/>
    </div>
  </div>
</template>

<style scoped></style>
