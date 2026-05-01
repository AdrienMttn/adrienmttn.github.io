<script setup lang="ts">
import { ref, onMounted } from "vue";
import gsap from "gsap";
import { ScrollToPlugin } from "gsap/ScrollToPlugin";

gsap.registerPlugin(ScrollToPlugin) 

const marquee = ref<HTMLElement | null>(null);

function scrollToSection(sectionId: string) {
  gsap.to(window, { duration: 1, scrollTo: `#${sectionId}` });
}
onMounted(() => {

  if (!marquee.value) return;
    gsap.to(marquee.value, {
      xPercent: -100,
      duration: 10,
      ease: "none",
      repeat: -1,
    });
});
</script>

<template>
  <footer id="contactSection" class="flex flex-col min-w-screen pt-20 gap-3 overflow-hidden">
    <div class="px-5 flex flex-col gap-3">
    <div class="w-sreen flex justify-between items-center">
      <p>(me suivre)</p>
      <p>(naviguer)</p>
    </div>
    <hr class="w-full h-1 bg-black rounded-2xl border-0" />
    <div class="flex justify-between items-center">
      <div class="flex flex-col justify-start items-start text-5xl">
        <a href="https://github.com/AdrienMttn" class=" hover:text-secondary transition-all duration-200 cursor-none">GITHUB</a>
        <a href="https://www.linkedin.com/in/adrien-metton" class=" hover:text-secondary transition-all duration-200 cursor-none">LINKEDIN</a>
        <a href="mailto:ametton.sio@gmail.com" class=" hover:text-secondary transition-all duration-200 cursor-none">EMAIL</a>
      </div>
      <div class="flex flex-col justify-end items-end text-5xl">
        <p @click="scrollToSection('aboutSection')" class=" hover:text-secondary transition-all duration-200 cursor-none">ABOUT</p>
        <p @click="scrollToSection('projectSection')" class=" hover:text-secondary transition-all duration-200 cursor-none">PROJECTS</p>
        <p @click="scrollToSection('contactSection')" class=" hover:text-secondary transition-all duration-200 cursor-none">CONTACT</p>
      </div>
    </div>
    </div>
    <div class="w-screen flex justify-center items-center">
      <p @click="scrollToSection('aboutSection')" class=" hover:text-secondary transition-all duration-200">retour en haut</p>
    </div>
    <div ref="marquee" class="h-50 flex items-center shrink-0">
      <h1 class="min-w-full uppercase font-bold text-[clamp(3.5rem,10vw,8rem)] leading-none">contactez moi</h1>
      <h1 class="min-w-full uppercase font-bold text-[clamp(3.5rem,10vw,8rem)] leading-none" aria-hidden="true">contactez moi</h1>
    </div>
    <div class="flex justify-between w-screen items-center px-5">
      <p class="text-sm">© 2026 - tous droits réservés</p>
      <p class="text-sm">Fait avec le ❤️</p>
    </div>
  </footer>
</template>

