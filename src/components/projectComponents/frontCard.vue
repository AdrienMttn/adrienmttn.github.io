<script setup lang="ts">
import { onMounted, ref } from "vue";
import language from "./language.vue";


const isHovered = ref(false);
const isOnline = ref(false);

const props = defineProps<{
  name: string;
  description: string;
  languages: string[];
  link: string;
  github: string;
  image: string;
  host: string;
  healthLink: string;
  haveDetails: boolean;
}>();



async function netlifyCheck(url: string): Promise<boolean> {
  const request = await fetch(url);
  const data = await request.json()
  if (data.published_deploy && data.published_deploy.state === "ready") {
    return true
  }
  return false
}

async function checkOnlineStatus(url: string): Promise<boolean> {
  const request = await fetch(url);
  const data = await request.json();
  if (data.status === 200) {
    return true;
  }
  return false;
}
onMounted(async ()=>{
  if (props.host === "Netlify") {
    isOnline.value = await netlifyCheck(props.healthLink);
  } else {
    isOnline.value = await checkOnlineStatus(props.healthLink);
  }
})
</script>

<template>
  <div class="project-card card h-[80vh] min-w-[80vw] lg:card-side shadow-sm relative overflow-hidden">
    <!-- 1. Image en arrière-plan -->
    <div
      class="absolute inset-0 bg-cover bg-center transition-transform duration-500 ease-in-out"
      :style="{ backgroundImage: `url(${props.image})` }"
    ></div>

    <!-- 2. Dégradé de fond -->
    <div
      class="absolute inset-0 transition-all duration-1000 ease-in-out bg-linear-to-r  from-40% from-white via-white/70 to-white/0 backdrop-blur-xl"
      :class="isHovered ? 'opacity-0' : 'opacity-100'"
    ></div>

    <!-- 3. Contenu textuel -->
    <div
      class="flex w-full relative transition-opacity duration-300 ease-in-out"
      :class="{ 'opacity-0': isHovered }"
    >
      <div class="p-10 w-[40%] h-full flex flex-col gap-10">
        <h2 class="text-4xl font-bold uppercase">{{ props.name }}</h2>
        <p class="text-justify">{{ props.description }}</p>
        <div class="flex gap-2 overflow-x-auto">
          <language v-for="lang in props.languages" :type="lang"/>
        </div>
        <div class="flex items-center gap-2">
          <div class="inline-grid *:[grid-area:1/1]">
            <div :class="isOnline ?'status-success' :  'status-error'" class="status animate-ping" ></div>
            <div :class="isOnline ?'status-success' :  'status-error'" class="status"></div>
          </div>
          <p>{{ isOnline ? 'En Ligne' : 'Hors Ligne' }}</p>
        </div>
        <div class="flex gap-4">
            <button v-if="props.haveDetails" class="btn btn-sm btn-outline cursor-none" @click="$emit('click:viewDetails')">Details</button>
            <a :href="props.link" target="_blank" :class="!isOnline ?'btn-disabled': ''" class="btn btn-sm btn-outline cursor-none">Voir le projet</a>
            <a :href="props.github" target="_blank" class="btn btn-sm btn-outline cursor-none">GitHub</a>
          </div>
      </div>
      <div class="w-[60%] h-full " @mouseenter="isHovered = true" @mouseleave="isHovered = false"></div>  
    </div>
  </div>
</template>