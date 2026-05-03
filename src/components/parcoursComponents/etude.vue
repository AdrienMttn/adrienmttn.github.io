<script setup lang="ts">
import gsap from 'gsap';
import { TextPlugin } from 'gsap/all';
import { ScrollTrigger } from 'gsap/all';
import { ref, type Ref, onMounted } from 'vue';

import etudeData from '../../data/etude.json';

import EtudeComponent from './etudeComponent/etude.vue';

gsap.registerPlugin(TextPlugin, ScrollTrigger);
const etudes = etudeData.etudes;
const lastEtude = etudes[etudes.length - 1];
if (lastEtude) {
  etudes.push({
    title: "",
    school: "",
    startYear: lastEtude.startYear + lastEtude.duration,
    duration: 0
  });
}
const title: Ref<HTMLHeadingElement | null> = ref(null);
// const container: Ref<HTMLDivElement | null> = ref(null);
const parcourList: Ref<HTMLUListElement | null> = ref(null);

onMounted(() => {
  // gsap.to(container.value, {
  //   scrollTrigger: {
  //     trigger: container.value,
  //     start: "top top",
  //     end: "bottom top",
  //     pin: true
  //   },
  // });
  gsap.to(title.value, {
    opacity: 1,
    text: "Mon parcours", 
    ease: "none",
    scrollTrigger: {
      trigger: title.value,
      start: "top 80%",
      end: "bottom 20%",
      toggleActions: "play none none reverse"
    },
  });

  gsap.from(parcourList.value, {
    opacity: 0,
    x: -100,
    scrollTrigger: {
      trigger: parcourList.value,
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
      gsap.to(title.value, { text:"", opacity: 0, duration: 0.5 });
    },
    onEnterBack: () => {
      // Quand on revient en scrollant vers le haut
      gsap.to(title.value, { text:"Mes études :",opacity: 1, duration: 0.5 });
    },
  });

  // ScrollTrigger pour la liste de la timeline
  ScrollTrigger.create({
    trigger: parcourList.value,
    start: "top 80%", // Commence quand le haut de la liste est à 80% du haut de l'écran
    end: "bottom 20%",
    onLeave: () => {
      // Quand on quitte la vue par le bas
      gsap.to(parcourList.value, { opacity: 0, scale: 0.8, duration: 0.5 });
    },
    onEnterBack: () => {
      // Quand on revient en scrollant vers le haut
      gsap.to(parcourList.value, { opacity: 1, scale: 1, duration: 0.5 });
    },
    onLeaveBack: () => {
        // Quand on quitte la vue par le haut
        gsap.to(parcourList.value, { opacity: 0, scale: 0.8, duration: 0.5 });
    },
    onEnter: () => {
        // Quand on entre dans la vue en scrollant vers le bas
        gsap.to(parcourList.value, { opacity: 1, scale: 1, duration: 0.5 });
    }
  });

});
</script>

<template>
  <div ref="container" class="h-screen bg-base-200">
    <div class="flex p-20 absolute">
      <h1 ref="title" class="text-3xl md:text-5xl font-bold">&nbsp;</h1>
    </div>
    <div class="w-full h-screen flex justify-center items-center">
    <ul ref="parcourList" class="timeline">
      <EtudeComponent v-for="(etude, index) in etudes" :key="index" :index="index" :title="etude.title" :school="etude.school" :startYear="etude.startYear" :duration="etude.duration" :listSize="etudes.length"/>
    </ul>
    </div>
  </div>
</template>