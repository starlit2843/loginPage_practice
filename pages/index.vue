<template>
    <div id="app" class="mx-auto flex grow flex-col overflow-auto bg-fullscreen flex h-full gap-[10vh] bg-[url('~/assets/images/HomepageBG.png')] px-9 py-[5vh] ">
      <div id="aa" class="flex justify-center items-center ">


        <div>
          <VOnboardingWrapper ref="wrapper" :steps="steps" />

          <div class="grid grid-cols-2 gap-10 place-items-center">
            <div id="login_Button" class=" shadow-special-cta-02 rounded-30 relative top-[80vh] login_Button" >
              <button @click="redirectToLogin" class=" rounded-30 px-6 py-2 hover:underline:hover">
                <span class="text-[4vw] text-white min-[512px]:text-xl">LOG IN
                </span>
              </button>
          </div>
          <div id="home_Button" class=" shadow-special-cta-02 rounded-30 relative top-[80vh] home_Button" >
            <button @click="redirectToHomePage" class=" rounded-30 px-6 py-2 hover:underline:hover">
                <span class="text-[4vw] text-white min-[512px]:text-xl">Home
                </span>
            </button>
            </div>
          </div>

        </div>

      </div>
    </div>

</template>

<script setup>
//import { ref } from 'vue';


import { ref, onMounted } from 'vue';
import { VOnboardingWrapper, useVOnboarding } from 'v-onboarding';
import 'v-onboarding/dist/style.css';


import '~/assets/css/tailwind base.css';
import{useRouter} from 'vue-router';

const router = useRouter();

function redirectToLogin(){
    router.push('/login');
}
function redirectToHomePage(){
  router.push('/home');
}


const wrapper = ref(null);
const { start, goToStep, finish } = useVOnboarding(wrapper);

const steps = ref([
  { 
    attachTo: { element: '#aa' }, 
    content: { title: 'Welcome to our Page!!' } 
  },
  { 
    attachTo: { element: '#login_Button' }, 
    content: { 
      title: 'Hit here to Log in!', 
    } 
  },
  { 
    attachTo: { element: '#home_Button' }, 
    content: { title: 'Go to Home Page!' } 
  }
]);

const options = ref({
  popper: {
    modifiers: [
      {
        name: 'offset',
        options: {
          offset: [0, 5]
        }
      }
    ]
  },
  labels: {
    previousButton: '上一步',
    nextButton: '下一步',
    finishButton: '完成'
  }
});

onMounted(() => {
  start();
});



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
    top: 80vh;
}
#home_Button{
    top: 80vh;
}
</style>

<style scoped>
  html{
    .login_Button:hover{
      background-color: #c4cee0;
    }
    .home_Button:hover{
      background-color: #9fb4a4;
    }

    .grid{
      display: grid
    }
    .grid-cols-2{
      grid-template-columns:repeat(2, minmax())
    }
  }
</style>
  