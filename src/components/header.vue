<script setup lang="ts">
import gsap from "gsap";
import { ScrollToPlugin } from "gsap/ScrollToPlugin";
gsap.registerPlugin(ScrollToPlugin) 
import { ref, type Ref, onMounted } from "vue";

const about: Ref<HTMLAnchorElement | null> = ref(null);
const projects: Ref<HTMLAnchorElement | null> = ref(null);
const contact: Ref<HTMLAnchorElement | null> = ref(null);


function scrollToSection(sectionId: string) {
  gsap.to(window, { duration: 1, scrollTo: `#${sectionId}` });
}
onMounted(() => {
  gsap.from(about.value, {
    duration: 0.5,
    opacity: 0,
    y: -20,
    ease: "power2.out",
  });
  gsap.from(projects.value, {
    duration: 1,
    opacity: 0,
    y: -20,
    delay: 0.5,
    ease: "power2.out",
  });
  gsap.from(contact.value, {
    duration: 1,
    opacity: 0,
    y: -20,
    delay: 1,
    ease: "power2.out",
  });
});
</script>

<template>
  <div ref="header" class="navbar fixed top-0 z-10 flex justify-center">
    <ul class="flex space-x-4 text-xl">
      <li ref="about" class="hover:text-secondary cursor-none">
        <a @click="scrollToSection('aboutSection')">About</a>
      </li>
      <li ref="projects" class="hover:text-secondary cursor-none ">
        <a @click="scrollToSection('projectSection')">Projects</a>
      </li>
      <li ref="contact" class="hover:text-secondary cursor-none">
        <a @click="scrollToSection('contactSection')">Contact</a>
      </li>
    </ul>
  </div>
</template>
