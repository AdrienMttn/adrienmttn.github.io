<script lang="ts" setup>
import competence from './competence.vue';

const props = defineProps<{
  details: {
    contexte: string;
    objectifs: string;
    pointsDeRealisation: string;
    difficultees: string;
    competences: { competence: string; sousCompetences: number }[];
  };
}>();
</script>

<template>
  <div class="project-card card h-[80vh] min-w-[80vw] lg:card-side shadow-sm relative overflow-y-scroll bg-base-100"> 
    <div class="p-10 h-full flex flex-col gap-10">
      <a @click="$emit('click:viewDetails')" class=" text-3xl hover:text-secondary transition-all duration-200 w-fit">&#8592; Retour</a>
      <div class="w-full">
        <h2 class="text-2xl font-bold uppercase">Contexte</h2>
        <p class="px-5 text-justify">{{ props.details.contexte }}</p>
      </div>
      <div class="w-full">
        <h2 class="text-2xl font-bold uppercase">Objectifs</h2>
        <p class="px-5 text-justify">{{ props.details.objectifs }}</p>
      </div>
      <div class="w-full">
        <h2 class="text-2xl font-bold uppercase">Points de Réalisation</h2>
        <p class="px-5 text-justify">{{ props.details.pointsDeRealisation }}</p>
      </div>
      <div class="w-full">
        <h2 class="text-2xl font-bold uppercase text-error">Difficultés</h2>
        <p class="px-5 text-justify">{{ props.details.difficultees }}</p>
      </div>
      <div>
        <h2 class="text-2xl font-bold uppercase">Competences</h2>
        <div class="flex flex-col gap-3 p-5">
          <competence v-for="uneCompetence in props.details.competences" :competence="uneCompetence.competence" :sousCompetences="uneCompetence.sousCompetences"/>
        </div>
      </div>
    </div>
  </div>
</template>