<script lang="ts" setup>
import { ref } from "vue";

const isHovered = ref(false);
const imageUrl = 'https://i.ibb.co/fdp8mxZw/Capture-d-e-cran-2026-04-16-a-12-40-59.png';
</script>

<template>
  <div class="card h-[80vh] lg:card-side shadow-sm relative overflow-hidden">
    <!-- 1. Image en arrière-plan -->
    <div
      class="absolute inset-0 bg-cover bg-center transition-transform duration-500 ease-in-out"
      :style="{ backgroundImage: `url(${imageUrl})` }"
    ></div>

    <!-- 2. Dégradé de fond -->
    <div
      class="absolute inset-0 transition-all duration-1000 ease-in-out bg-linear-to-r  from-40% from-white via-white/70 to-white/0"
      :class="isHovered ? 'opacity-0' : 'opacity-100'"
    ></div>

    <!-- 3. Contenu textuel -->
    <div
      class="flex w-full relative transition-opacity duration-300 ease-in-out"
      :class="{ 'opacity-0': isHovered }"
    >
      <div class="p-10 w-[40%] h-full flex flex-col justify-between">
        <h2 class="text-4xl font-bold">Vibz</h2>
        <p class="text-justify">Vibz est une application web moderne qui vous permet de découvrir et d'écouter le Top 20 des musiques les plus populaires de la semaine sur YouTube.</p>
      </div>
      <div class="w-[60%] h-full cursor-pointer" @mouseenter="isHovered = true" @mouseleave="isHovered = false"></div>  
    </div>
  </div>
</template>