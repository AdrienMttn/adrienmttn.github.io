<script lang="ts" setup>

const props = defineProps<{
  title: string;
  school: string;
  startYear: number;
  duration: number;
  listSize: number;
  index: number;
}>();
</script>

<template>
  <li class="timeline-item">
    <hr v-if="index != 0"/>
    <div class="timeline-start">{{ props.startYear }}</div>
      <div class="timeline-middle">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 20 20"
          fill="currentColor"
          class="h-5 w-5"
        >
          <circle cx="10" cy="10" r="8" stroke="#000"></circle>
        </svg>
      </div>
      <div class=" col-start-4 row-start-3" v-if="listSize != index+1">
        <h1 class="text-1xl md:text-3xl font-bold w-100 gsap-text">
          {{ props.title }}
        </h1>
      <p class="gsap-text">{{ props.school }}</p>
    </div>
    <hr v-if="listSize != index+1"/>
  </li>
</template>