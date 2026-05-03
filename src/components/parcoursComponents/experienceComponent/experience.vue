<script setup lang="ts">
import { ref } from 'vue';
const props = defineProps<{ company: string; type: string; desc: string;}>();
const isHovered = ref(false);
</script>

<template>
  <div class="experience flex justify-between w-screen h-fit border-b py-1.5 px-22 " @mouseenter="isHovered = true" @mouseleave="isHovered = false">
    <h1 :class="isHovered ? 'text-secondary ml-10' : ''" class="w-1/2 text-6xl font-bold transition-all duration-300">{{ props.company }}</h1>
    <div :class="isHovered ? 'mr-25' : ''" class="flex flex-col items-end w-1/2 transition-all duration-300">
      <p class="text-xl">{{ props.type }}</p>
      <p class="text-[15px] max-w-full">{{ props.desc }}</p>
    </div>
  </div>
</template>