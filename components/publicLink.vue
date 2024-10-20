<template>
    
      <a :href="link" rel="noopener noreferrer" target="_blank" class="flex flex-col gap-1">
        <span class="truncate rounded-full bg-base px-4 py-2 text-base-content shadow-special-cta-02">
          {{ link }}
        </span>
      </a>
 
  </template>
  
  <script setup>
  const props = defineProps({
    link: {
      type: String,
      required: true,
    },
  });
  </script>