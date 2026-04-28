<script setup lang="ts">
import { gsap } from "gsap";
import {ref, type Ref, onMounted} from "vue";
import UneExperience from "./experienceComponent/experience.vue";
import experienceData from "../../data/experience.json";

const experiences = experienceData.experiences;
const title: Ref<HTMLHeadingElement | null> = ref(null);
onMounted(() => {

  gsap.to(title.value, {
    opacity: 1,
    text: "Mes expériences :", 
    ease: "none",
    scrollTrigger: {
      trigger: title.value,
      start: "top 80%",
      end: "bottom 20%",
      toggleActions: "play none none reverse"
    },
  });
});


</script>

<template>
  <div ref="container" class="bg-base-200">
    <div class="absolute pl-20">
      <h1 ref="title" class="text-3xl md:text-5xl font-bold"></h1>
    </div>
    <div class="w-screen h-screen flex justify-center items-center">
      <div class="flex flex-col gap-5">
        <UneExperience v-for="experience in experiences" :company="experience.company" :type="experience.type" :desc="experience.description"/>
      </div>
    </div>
  </div>
</template>