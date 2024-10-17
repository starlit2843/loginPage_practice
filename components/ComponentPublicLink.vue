<template>
    <div class="flex flex-col gap-1">
      <h1 class="font-bold text-base text-base-100">公開連結</h1>
      <a :href="link" rel="noopener noreferrer" target="_blank" class="flex flex-col gap-1">
        <span class="truncate rounded-full bg-base px-4 py-2 text-base-content shadow-special-cta-02">
          {{ link }}
        </span>
      </a>
    </div>
  </template>
  
  <script setup>
  import { defineProps } from 'vue';
  
  const props = defineProps({
    link: {
      type: String,
      required: true,
    },
  });
  </script>