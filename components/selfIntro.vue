<template>

        <div class="min-h-[5rem] break-all rounded-lg bg-base px-6 pt-3 pb-5 text-base-content shadow-special-cta-02">
                {{ intro }}
        </div>
</template>

<script setup>
const props = defineProps({
    intro:{
        type: String,
        required: true
    }
})
</script>