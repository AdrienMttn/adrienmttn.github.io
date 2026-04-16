<script setup lang="ts">
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import {ref, type Ref, onMounted} from "vue";
import UneExperience from "./experienceComponent/experience.vue";
import experienceData from "../../data/experience.json";

const experiences = experienceData.experiences;
const listExperience: Ref<HTMLDivElement | null> = ref(null);
const container: Ref<HTMLDivElement | null> = ref(null);
const title: Ref<HTMLHeadingElement | null> = ref(null);
onMounted(() => {
  gsap.to(container.value, {
    scrollTrigger: {
      trigger: container.value,
      start: "top top",
      end: "bottom 50%",
      markers: false,
      pin: true
    },
  });

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

  ScrollTrigger.create({
    trigger: title.value,
    start: "top top", // Commence quand le haut du titre est à 20% du haut de l'écran
    end: "bottom bottom", // Termine quand le bas du titre est à 20% du haut de l'écran
    onLeave: () => {
      // Quand on quitte la vue par le haut
      gsap.to(title.value, { text:"", opacity: 0, duration: 0.5});
    },
    onEnterBack: () => {
      // Quand on revient en scrollant vers le haut
      gsap.to(title.value, { text:"Mes expériences :", opacity:1 , duration: 0.5 });
    },
  });
  if (listExperience.value) {
    const experiences = listExperience.value.querySelectorAll(".experience");
    experiences.forEach((experience) => {
      ScrollTrigger.create({
        trigger: experience,
        start: "50% 50%",
        end: "bottom+=50 50%",
        markers: true,
        onEnter: () => {
          gsap.to(experience, {
            scale:1.25,
            gap: "270px",
            opacity: 1,
          });
        },
        onEnterBack: () => {
          gsap.to(experience, {
            scale:1.25,
            gap: "270px",
            opacity: 1,
        });
        },
         onLeave: () => {
          gsap.to(experience, {
            scale: 0.75,
            gap: "220px",
            opacity: 0.5,
        });
      },
        onLeaveBack: () => {
          gsap.to(experience, {
            scale: 0.75,
            gap: "220px",
            opacity: 0.5,
        });
      },
    });
  });
}
});


</script>

<template>
  <div ref="container" class="w-sreen h-screen bg-base-200">
    <div class="absolute flex p-20 ">
      <h1 ref="title" class="text-3xl md:text-5xl font-bold"></h1>
    </div>
    <div class="w-screen h-screen flex justify-center items-center">
    <div ref="listExperience" class="relative h-fit w-screen flex justify-center items-center">
      <div class="flex flex-col gap-15 justify-center items-center">
        <UneExperience v-for="experience in experiences" :company="experience.company" :type="experience.type" :desc="experience.description"/>
      </div>
    </div>
    </div>
  </div>
</template>