<template>
        <h1 class="font-bold text-base text-base-100">{{ titleWord }}</h1>
</template>

<script setup>
    const props = defineProps({
        titleWord:{
            type:String,
            required:true
        }
    });
</script>