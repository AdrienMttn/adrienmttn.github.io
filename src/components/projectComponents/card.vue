<script lang="ts" setup>
import { ref } from "vue";
import frontCard from "./frontCard.vue";
import backCard from "./backCard.vue";

const viewDetails = ref(false);

function toggleDetails() {
  viewDetails.value = !viewDetails.value;
  console.log("Toggled view details:", viewDetails.value);
}


const props = defineProps<{
  name: string;
  description: string;
  languages: string[];
  link: string;
  github: string;
  image: string;
  host: string;
  healthLink: string;
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
  @click:viewDetails="viewDetails = true"
  />
  <back-card v-else @click:viewDetails="viewDetails = false"/>
</template>