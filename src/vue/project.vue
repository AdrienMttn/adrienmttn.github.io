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
    gsap.to(title.value, {
    opacity: 1,
    text: "Mes Projets",
    ease: "none",
    scrollTrigger: {
      trigger: title.value,
      start: "top 80%",
      end: "bottom 20%",
      toggleActions: "play none none reverse"
      },
    });
  }
  if (projectList.value) {
    const distance = projectList.value.scrollWidth - window.innerWidth + 80;

    gsap.set(projectList.value, { opacity: 0 });
    
    gsap.to(projectList.value, {
    opacity: 1,
    ease: "none",
    scrollTrigger: {
      trigger: title.value,
      start: "top+=50 80%",
      end: "bottom 20%",
      toggleActions: "play none none reverse"
      },
    });

    gsap.to(projectList.value,{
      x: () => -distance,
      ease: "none",
      scrollTrigger: {
        trigger: container.value,
        start: "top-=30 top",
        end: () => `+=${distance}`,
        pin: true, 
        scrub: true,
        invalidateOnRefresh: true,
      },
    });
  }
  
});
</script>

<template>
  <div id="projectSection" ref="container" class="w-screen h-screen flex flex-col gap-10 bg-base-200 overflow-hidden">
    <div class="flex pl-20">
        <h1 ref="title" class="text-3xl md:text-5xl font-bold">&nbsp;</h1>
    </div>
    <div ref="projectList" class="pl-40 pr-40 flex gap-20 w-screen">
      <card v-for="project in projects" :name="project.name" :description="project.description" :languages="project.languages" :link="project.link" :github="project.github" :image="project.image" :host="project.host" :healthLink="project.healthLink" :details="project?.details"/>
    </div>
  </div>
</template>