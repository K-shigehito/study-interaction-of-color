<script lang="ts">
import { defineComponent } from '@vue/runtime-core';
import LighterAndOrDarker from '../components/LighterAndOrDarker.vue';
import ReversedGrounds from '../components/ReversedGrounds.vue';

export default defineComponent({
  components: {
    LighterAndOrDarker,
    ReversedGrounds,
  },
});
</script>
<template>
  <div class="m-[12px]">
    <h2 class="text-[24px] font-bold">Lighter and / or darker</h2>
    <div class="mt-[12px]">
      <LighterAndOrDarker />
    </div>
  </div>
  <div class="mt-[40px] m-[12px]">
    <h2 class="text-[24px] font-bold">looking like the reversed grounds</h2>
    <div class="mt-[12px]">
      <ReversedGrounds />
    </div>
  </div>
</template>
