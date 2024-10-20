<template>
    <div class="h-[100vh] mx-auto flex max-w-lg grow flex-col overflow-auto">
      <div class="flex h-full flex-col gap-[10vh] overflow-y-scroll bg-[url('~/assets/images/UserPageBackground.png')] px-9 py-[5vh]">
        <div class="flex w-full flex-row items-center justify-center">
          <img :src="logoSrc" alt="NCCU Logo">
        </div>
        <div class="flex flex-col gap-10">
          <div class="flex flex-col gap-7">
            <div class="flex flex-row items-center justify-between px-4">
              <div class="flex flex-col content-between gap-2">
                <span class="text-5xl font-bold">{{ username }}</span>
                <span class="text-2xl text-info-content">{{ userTag }}</span>
              </div>
              <img src="/assets/images/EmptyUser.26402e9e.png" class="h-24 w-24" alt="user pic">
            </div>
            <div class="h-8"></div>
            <div class="flex flex-col gap-1">
            <ComponentSelfIntro :intro ="introduction"></ComponentSelfIntro>
            </div>
          </div>
          <div class="flex flex-col gap-5">

                <!--<h1 class="font-bold text-base text-base-100"> 公開連結 </h1>
                <a :href="link" rel="noopener noreferrer" target="_blank" class="flex flex-col gap-1">
                  <span class="truncate rounded-full bg-base px-4 py-2 text-base-content shadow-special-cta-02">
                    {{ link }}
                  </span>
                </a>-->
            
                <ComponentPublicLink :link="link" />
          </div>
        </div>            
      </div>
    </div>

  </template>
  
  <script setup>
  import { ref } from 'vue';
  //import img from '~/assets/images/EmptyUser.26402e9e.png';
  import '~/assets/css/tailwind base.css';
  import ComponentPublicLink from '~/components/publicLink.vue';
  import ComponentSelfIntro from '~/components/selfIntro.vue';
  
  const logoSrc = 'data:image/png;base64,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';
  const username = ref('如');
  const userTag = ref('@lulu');
  const introduction = ref('Hello World! ^_^');
  const link = ref('https://www.google.com.tw/?hl=zh_TW');

  </script>