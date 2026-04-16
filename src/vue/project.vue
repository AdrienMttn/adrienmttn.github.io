<script setup lang="ts">
import card from "../components/projectComponents/card.vue";
</script>

<template>
  <div ref="container" class="w-sreen h-[300vh] bg-base-200">
    <div class="absolute z-30 flex p-20 ">
        <h1 ref="title" class="text-3xl md:text-5xl font-bold">Mes projets :</h1>
    </div>
    <div ref="card" class="p-40">
      <card/>
    </div>
  </div>
</template>