<script lang="ts">
import { defineComponent, ref, computed } from '@vue/runtime-core';
import { useTransition } from '@vueuse/core';

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

    const transitionSpeed = ref(10);
    const duration = computed(() => transitionSpeed.value);

    const baseNumber = ref(0);
    const translateNumber = useTransition(baseNumber, {
      duration: duration,
    });
    const toggleTransition = () => {
      baseNumber.value = baseNumber.value === 20 ? 0 : 20;
    };
    const toggleColorPosition = () => {
      [firstColor.value, secondColor.value] = [
        secondColor.value,
        firstColor.value,
      ];
    };

    return {
      firstColor,
      secondColor,
      firstColorStyle,
      secondColorStyle,
      transitionSpeed,
      translateNumber,
      toggleTransition,
      toggleColorPosition,
    };
  },
});
</script>
<template>
  <!-- 解説部分 -->
  <div class="flex w-[820px] p-[40px] border-[1px] border-gray-800">
    <div
      class="
        grid grid-cols-1 grid-rows-1
        items-center
        justify-items-center
        w-[170px]
        h-[170px]
      "
    >
      <div class="justify-self-start ml-[20px] col-start-1 row-start-1 z-10">
        A
      </div>
      <div
        class="
          col-start-1
          row-start-1
          w-[120px]
          h-[120px]
          transform
          rotate-45
          bg-white
          border-[1px] border-gray-800
        "
      ></div>
    </div>
    <div
      class="
        grid grid-cols-1 grid-rows-1
        items-center
        justify-items-center
        w-[170px]
        h-[170px]
        -translate-x-16
      "
    >
      <div class="justify-self-start ml-[20px] col-start-1 row-start-1 z-10">
        B
      </div>
      <div
        class="
          col-start-1
          row-start-1
          w-[120px]
          h-[120px]
          transform
          rotate-45
          bg-white
          border-[1px] border-gray-800
        "
      ></div>
    </div>

    <div
      class="
        relative
        grid grid-cols-1 grid-rows-1
        items-center
        justify-items-center
        w-[170px]
        h-[170px]
      "
    >
      <div class="justify-self-start ml-[20px] col-start-1 row-start-1 z-10">
        A
      </div>
      <div
        class="
          col-start-1
          row-start-1
          w-[120px]
          h-[120px]
          transform
          rotate-45
          bg-white
          border-[1px] border-gray-800
        "
      ></div>
      <div
        class="
          absolute
          right-0
          grid grid-cols-1 grid-rows-1
          items-center
          justify-items-center
          transform
        "
      >
        <div class="justify-self-center col-start-1 row-start-1 z-10">C</div>
        <div
          class="
            col-start-1
            row-start-1
            mx-[12px]
            w-[50px]
            h-[50px]
            transform
            rotate-45
            bg-white
            border-dashed border-l-[1px] border-b-[1px] border-gray-800
          "
        ></div>
      </div>
    </div>

    <div class="h-[170px] mx-[12px] text-[18px] leading-[170px]">---></div>

    <div
      class="
        grid grid-cols-1 grid-rows-1
        items-center
        justify-items-center
        w-[170px]
        h-[170px]
      "
    >
      <div class="justify-self-start ml-[20px] col-start-1 row-start-1 z-10">
        B
      </div>
      <div
        class="
          col-start-1
          row-start-1
          w-[120px]
          h-[120px]
          transform
          rotate-45
          bg-white
          border-[1px] border-gray-800
        "
      ></div>
    </div>
  </div>

  <!-- プレビュー部分 -->
  <div class="flex w-[820px] mt-[12px] p-[40px] border-[1px] border-gray-800">
    <div
      class="
        grid grid-cols-1 grid-rows-1
        items-center
        justify-items-center
        w-[170px]
        h-[170px]
      "
    >
      <div
        :style="firstColorStyle"
        class="
          col-start-1
          row-start-1
          w-[120px]
          h-[120px]
          transform
          rotate-45
          bg-gray-100
        "
      ></div>
    </div>

    <div
      class="
        relative
        grid grid-cols-1 grid-rows-1
        items-center
        justify-items-center
        w-[170px]
        h-[170px]
        -translate-x-16
      "
      :style="{ left: translateNumber + '%' }"
    >
      <div
        :style="secondColorStyle"
        class="
          col-start-1
          row-start-1
          w-[120px]
          h-[120px]
          transform
          rotate-45
          bg-gray-400
        "
      ></div>
    </div>
  </div>

  <!-- コントローラー -->
  <div class="mt-[12px]">
    <button
      type="button"
      class="
        mr-[8px]
        px-[12px]
        py-[4px]
        rounded-[4px]
        text-gray-100
        bg-gray-600
        hover:opacity-90
      "
      @click="toggleTransition"
    >
      move
    </button>
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
      speed：
      <input
        v-model="transitionSpeed"
        type="number"
        class="p-[4px] w-[80px] border-[1px] border-gray-800"
      />
      ミリ秒
    </div>
  </div>
</template>
