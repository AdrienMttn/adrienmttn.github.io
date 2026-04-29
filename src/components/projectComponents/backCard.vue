<script lang="ts" setup>
import competence from './competence.vue';
</script>

<template>
  <div class="project-card card h-[80vh] min-w-[80vw] lg:card-side shadow-sm relative overflow-y-scroll bg-base-100"> 
    <div class="p-10 h-full flex flex-col gap-10">
      <a @click="$emit('click:viewDetails')" class="cursor-pointer text-3xl hover:text-secondary transition-all duration-200 w-fit">&#8592; Retour</a>
      <div class="w-full">
        <h2 class="text-2xl font-bold uppercase">Contexte</h2>
        <p class="px-5">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Fugiat exercitationem cupiditate qui corrupti quis, velit dolorem nisi, modi distinctio molestiae esse expedita amet optio consectetur tempore neque quidem! Sequi, aliquam!</p>
      </div>
      <div class="w-full">
        <h2 class="text-2xl font-bold uppercase">Objectifs</h2>
        <p class="px-5">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Fugiat exercitationem cupiditate qui corrupti quis, velit dolorem nisi, modi distinctio molestiae esse expedita amet optio consectetur tempore neque quidem! Sequi, aliquam!</p>
      </div>
      <div class="w-full">
        <h2 class="text-2xl font-bold uppercase">Points de Réalisation</h2>
        <p class="px-5">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Fugiat exercitationem cupiditate qui corrupti quis, velit dolorem nisi, modi distinctio molestiae esse expedita amet optio consectetur tempore neque quidem! Sequi, aliquam!</p>
      </div>
      <div class="w-full">
        <h2 class="text-2xl font-bold uppercase text-error">Difficultés</h2>
        <p class="px-5">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Fugiat exercitationem cupiditate qui corrupti quis, velit dolorem nisi, modi distinctio molestiae esse expedita amet optio consectetur tempore neque quidem! Sequi, aliquam!</p>
      </div>
      <div>
        <h2 class="text-2xl font-bold uppercase">Competences</h2>
        <div class="flex flex-col gap-3 p-5">
          <competence competence="A" :sousCompetences="0"/>
          <competence competence="B" :sousCompetences="2"/>
          <competence competence="F" :sousCompetences="1"/>
          <competence competence="C" :sousCompetences="2"/>
        </div>
      </div>
    </div>
  </div>
</template>