<script lang="ts">
import { defineComponent, ref, computed } from '@vue/runtime-core';
// import { useTransition } from '@vueuse/core';

export default defineComponent({
  setup() {
    const firstColor = ref('#F5F5F5');
    const firstColorStyle = computed(() =>
      firstColor.value ? `background-color: ${firstColor.value}` : ''
    );

    const secondColor = ref('#DCDCDC');
    const secondColorStyle = computed(() =>
      secondColor.value ? `background-color: ${secondColor.value}` : ''
    );

    const thirdColor = ref('#CCCCCC');
    const thirdColorStyle = computed(() =>
      thirdColor.value ? `background-color: ${thirdColor.value}` : ''
    );

    const toggleColorPosition = () => {
      [firstColor.value, secondColor.value] = [
        secondColor.value,
        firstColor.value,
      ];
    };

    return {
      firstColor,
      firstColorStyle,
      secondColor,
      secondColorStyle,
      thirdColor,
      thirdColorStyle,
      toggleColorPosition,
    };
  },
});
</script>
<template>
  <!-- プレビュー部分 -->
  <div class="flex w-[820px] mt-[12px] p-[40px] border-[1px] border-gray-800">
    <div
      :style="firstColorStyle"
      class="flex items-center justify-center w-[280px] h-[340px]"
    >
      <div :style="thirdColorStyle" class="w-[70px] h-[85px]"></div>
    </div>
    <div
      :style="secondColorStyle"
      class="flex items-center justify-center w-[280px] h-[340px]"
    >
      <div :style="thirdColorStyle" class="w-[70px] h-[85px]"></div>
    </div>
  </div>

  <!-- コントローラー -->
  <div class="mt-[12px]">
    <button
      type="button"
      class="
        px-[12px]
        py-[4px]
        rounded-[4px]
        text-gray-100
        bg-gray-600
        hover:opacity-90
      "
      @click="toggleColorPosition"
    >
      change
    </button>
    <div class="mt-[8px]">
      color A：
      <input
        v-model="firstColor"
        type="text"
        class="p-[4px] border-[1px] border-gray-800"
      />
    </div>
    <div class="mt-[8px]">
      color B：
      <input
        v-model="secondColor"
        type="text"
        class="p-[4px] border-[1px] border-gray-800"
      />
    </div>
    <div class="mt-[8px]">
      color C：
      <input
        v-model="thirdColor"
        type="text"
        class="p-[4px] border-[1px] border-gray-800"
      />
    </div>
  </div>
</template>
