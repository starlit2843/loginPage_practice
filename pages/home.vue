<template>
    
     <div class="h-[100vh] mx-auto flex max-w-lg grow flex-col overflow-auto">
        <div class="flex h-full flex-col gap-[10vh] overflow-y-scroll bg-[url('~/assets/images/UserPageBackground.png')] px-9 py-[5vh]">
            <div class="items-center justify-center">
                <ComponentSwiper></componentSwiper>
            </div>
        </div>
    </div>


    
    <div v-if="isGuideActive" class="guide-overlay">
      <!-- 高亮區域 -->
      <div
        v-if="currentElementPosition"
        :style="highlightStyle"
        class="highlight"
      ></div>

      <!-- 引導文本 -->
      <div :style="guideTextStyle" class="guide-text">
        <p>{{ steps[currentStep].text }}</p>
        <button @click="nextStep">下一步</button>
      </div>
    </div>

    <!-- 其他頁面內容 -->
    <div id="app-content">
      <div ref="step1" class="step">步驟1：這是第一步內容</div>
      <div ref="step2" class="step">步驟2：這是第二步內容</div>
      <div ref="step3" class="step">步驟3：這是第三步內容</div>
    </div>



</template>

<script setup>
    import ComponentSwiper from '~/components/swiper.vue';

    import { ref, onMounted, watch, computed, nextTick } from "vue";

// 定義步驟內容
const steps = [
  { refName: "step1", text: "這是第一步：了解基本操作" },
  { refName: "step2", text: "這是第二步：熟悉介面功能" },
  { refName: "step3", text: "這是第三步：開始使用應用" },
];

// 當前步驟索引
const currentStep = ref(0);
const isGuideActive = ref(true);
const currentElementPosition = ref(null);

// 保存 DOM 元素的參考
const stepRefs = {
  step1: ref(null),
  step2: ref(null),
  step3: ref(null),
};

// 更新高亮區域位置
const updateHighlightPosition = () => {
  const step = steps[currentStep.value];
  const element = stepRefs[step.refName].value;
  if (element) {
    currentElementPosition.value = element.getBoundingClientRect();
  }
};

// 計算高亮區域的樣式
const highlightStyle = computed(() => {
  if (currentElementPosition.value) {
    const { top, left, width, height } = currentElementPosition.value;
    return {
      top: `${top + window.scrollY}px`,
      left: `${left + window.scrollX}px`,
      width: `${width}px`,
      height: `${height}px`,
      position: "absolute",
      backgroundColor: "rgba(255, 255, 255, 0.3)",
      border: "2px solid #f39c12",
      zIndex: 10,
    };
  }
  return {};
});

// 計算引導文字的位置和樣式
const guideTextStyle = computed(() => {
  if (currentElementPosition.value) {
    const { bottom, left } = currentElementPosition.value;
    return {
      position: "absolute",
      top: `${bottom + window.scrollY + 10}px`,
      left: `${left + window.scrollX}px`,
      backgroundColor: "#fff",
      padding: "1rem",
      borderRadius: "5px",
      boxShadow: "0px 4px 8px rgba(0, 0, 0, 0.3)",
      zIndex: 20,
    };
  }
  return {};
});

// 下一步
const nextStep = () => {
  if (currentStep.value < steps.length - 1) {
    currentStep.value++;
    nextTick(updateHighlightPosition);
  } else {
    isGuideActive.value = false;
  }
};

// 當 currentStep 改變時，重新計算高亮位置
watch(currentStep, () => {
  nextTick(updateHighlightPosition);
});

// 在組件掛載後設置第一步的高亮區域
onMounted(() => {
  updateHighlightPosition();
});
</script>
