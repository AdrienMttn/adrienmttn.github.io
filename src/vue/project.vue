<script setup lang="ts">
import { ref, onMounted } from "vue";
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
import card from "../components/projectComponents/card.vue";
import projectData from "../data/project.json";

const title = ref<HTMLElement | null>(null);
const container = ref<HTMLElement | null>(null);
const projectList = ref<HTMLElement | null>(null);
const projects = projectData.projects;

gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
  if (title.value) {
  //   gsap.to(title.value, {
  //   opacity: 1,
  //   text: "Mes Projets :",
  //   ease: "none",
  //   scrollTrigger: {
  //     trigger: title.value,
  //     start: "top 80%",
  //     end: "bottom 20%",
  //     toggleActions: "play none none reverse"
  //   },
  // });

    gsap.to(title.value, {
      scrollTrigger: {
        markers: true,
        trigger: container.value,
        start: "top+=50 top",
        end: "bottom top",
        pin: title.value,
      },
    });
  }
  // if (container.value)
  // {
  //   gsap.to(container.value, {
  //     scrollTrigger: {
  //       trigger: container.value,
  //       start: "top+=50 top",
  //       end: "bottom top",
  //       pin: true,
  //     },
  //   });
  // }
  
});
</script>

<template>
  <div ref="container" class="flex flex-col gap-10 bg-base-200">
    <div class="flex pl-20">
        <h1 ref="title" class="text-3xl md:text-5xl font-bold">Mes Projets :</h1>
    </div>
    <div ref="projectList" class="pl-40 pr-40 flex flex-col gap-20">
      <card v-for="project in projects" :name="project.name" :description="project.description" :languages="project.languages" :link="project.link" :github="project.github" :image="project.image" :host="project.host" :healthLink="project.healthLink"/>
    </div>
  </div>
</template>