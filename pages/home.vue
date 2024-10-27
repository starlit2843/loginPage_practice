<template>
    
     <div class="h-[100vh] mx-auto flex max-w-lg grow flex-col overflow-auto">
        <div class="flex h-full flex-col gap-[10vh] overflow-y-scroll bg-[url('~/assets/images/UserPageBackground.png')] px-9 py-[5vh]">
            <div class="items-center justify-center">
                <ComponentSwiper></componentSwiper>
            </div>
        </div>
    </div>
</template>

<script setup>
    import ComponentSwiper from '~/components/swiper.vue';
</script>
