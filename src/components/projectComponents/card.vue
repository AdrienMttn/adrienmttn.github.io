<script lang="ts" setup>
import { ref } from "vue";
import frontCard from "./frontCard.vue";
import backCard from "./backCard.vue";

const viewDetails = ref(false);


const props = defineProps<{
  name: string;
  description: string;
  languages: string[];
  link: string;
  github: string;
  image: string;
  host: string;
  healthLink: string;
  details?: {
    contexte: string;
    objectifs: string;
    pointsDeRealisation: string;
    difficultees: string;
    competences: { competence: string; sousCompetences: number }[];
  } | null;
}>();

</script>

<template>
  <front-card 
  v-if="!viewDetails"
  :name="props.name"
  :description="props.description"
  :languages="props.languages"
  :link="props.link"
  :github="props.github"
  :image="props.image"
  :host="props.host"
  :healthLink="props.healthLink"
  :have-details="props.details ? true : false"
  @click:viewDetails="viewDetails = true"
  />
  <back-card v-else-if="props.details && viewDetails" @click:viewDetails="viewDetails = false" :details="props.details"/>
</template>