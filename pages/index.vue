<template>
    <div id="app" class="mx-auto flex grow flex-col overflow-auto bg-fullscreen flex h-full gap-[10vh] bg-[url('~/assets/images/HomepageBG.png')] px-9 py-[5vh] ">
        <div id="login_Button" class="place-self-center shadow-special-cta-02 rounded-30 absolute top-[80vh] login_Button" >
            <button @click="redirectToLogin" class="place-self-center rounded-30 px-6 py-2 hover:underline:hover">
                <span class="text-[4vw] text-white min-[512px]:text-xl">LOG IN
                </span>
            </button>
            
        </div>
    
    </div>

</template>

<script setup>
//import { ref } from 'vue';
import '~/assets/css/tailwind base.css';
import{useRouter} from 'vue-router';

const router = useRouter();

function redirectToLogin(){
    router.push('/login');
}
</script>

<style>
html, body, #app {
  height: 100%;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
}
body {
  width: 100%;
  height: 100%;
  margin: 0;
}
#app {
  height: 100vh; /* 設置最小高度為100%視口高度 */
}

#login_Button{
    top: 80%;
}
</style>

<style scoped>
  html{
    .login_Button:hover{
      background-color: #c4cee0;
    }
  }
</style>
  