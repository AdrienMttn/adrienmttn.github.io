<script setup lang="ts">
  const props = defineProps<{ company: string; type: string; desc: string;}>();
</script>

<template>
  <div class="experience flex gap-55 items-center opacity-50 scale-75">
    <h1 class="text-3xl font-bold w-100 text-right">{{ props.company }}</h1>
    <div class="flex flex-col w-100 text-left">
      <p>{{ props.type }}</p>
      <p class="text-[6px]">{{ props.desc }}</p>
    </div>
  </div>
</template>