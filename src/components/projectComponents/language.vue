<script lang="ts" setup>
const listLanguageWithStyle: { [key: string]: string } = {
  "HTML" : "text-orange-500 border-orange-500" ,
  "CSS" : "text-blue-500 border-blue-500" ,
  "JavaScript" : "text-yellow-500 border-yellow-500" ,
  "TypeScript": "text-blue-700 border-blue-700" ,
  "Vue.js" : "text-green-500 border-green-500" ,
  "GO" : "text-cyan-500 border-cyan-500" ,
  "PHP" : "text-purple-500 border-purple-500" ,
  "SQL" : "text-gray-500 border-gray-500" ,
};
const props = defineProps<{type : string}>();
</script>

<template>
  <div :class="listLanguageWithStyle[props.type] + ' px-4 py-2 rounded-full text-sm font-bold border'">
    {{ props.type }}

  </div>
</template>