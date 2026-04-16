<script setup lang="ts">
import { gsap } from "gsap";
import { TextPlugin } from "gsap/TextPlugin";
import { ScrollTrigger } from "gsap/all";
import { ref, type Ref, onMounted } from "vue";

gsap.registerPlugin(TextPlugin, ScrollTrigger);

const img: Ref<HTMLDivElement | null> = ref(null);
const title: Ref<HTMLHeadingElement | null> = ref(null);

onMounted(() => {
  gsap.from(img.value, {
    duration: 2,
    opacity: 0,
    scale: 0.1,
    ease: "power2.out",
  });
  gsap.to(title.value, {
    duration: 1,
    opacity: 1,
    text: "Adrien Metton",
  });
  ScrollTrigger.create({
    trigger: img.value,
    start: "top 80%",
    end: "bottom 20%",
    onLeave: () => {
      gsap.to(img.value, {
        duration: 1,
        opacity: 0,
        scale: 0.1,
        ease: "power2.out",
      });
    },
    onEnterBack: () => {
      gsap.to(img.value, {
        duration: 1,
        opacity: 1,
        scale: 1,
        ease: "power2.out",
      });
    },
  });

  ScrollTrigger.create({
    trigger: title.value,
    start: "top 80%",
    end: "bottom 20%",
    onLeave: () => {
      gsap.to(title.value, {
        duration: 1,
        opacity: 0,
        text: "",
        ease: "power2.out",
      });
    },
    onEnterBack: () => {
      gsap.to(title.value, {
        duration: 1,
        opacity: 1,
        text: "Adrien Metton",
        ease: "power2.out",
      });
    },
  });
});
</script>

<template>
  <div ref="main" class="hero bg-base-200 min-h-screen">
    <div class="hero-content text-center">
      <div class="max-w-md">
        <div ref="img" class="hover-3d">
          <figure class="">
            <img
              class="mask mask-hexagon w-50 hover-3d"
              src="https://i.ibb.co/GfrpzYrz/365044476-958753211856596-815558572893089781-n.jpg"
            />
          </figure>
          <div></div>
          <div></div>
          <div></div>
          <div></div>
          <div></div>
          <div></div>
          <div></div>
          <div></div>
        </div>
        <h1 ref="title" class="text-3xl md:text-5xl font-bold"></h1>
      </div>
    </div>
  </div>
</template>
