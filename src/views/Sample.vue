<script lang="ts">
import { defineComponent } from '@vue/runtime-core';
import LighterAndOrDarkerVue from '../components/LighterAndOrDarker.vue';

export default defineComponent({
  components: {
    LighterAndOrDarkerVue,
  },
});
</script>
<template>
  <div class="m-[12px]">
    <h2 class="text-[24px] font-bold">Lighter and / or darker</h2>
    <div class="mt-[12px]">
      <LighterAndOrDarkerVue />
    </div>
  </div>
</template>
