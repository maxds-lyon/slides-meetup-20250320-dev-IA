<template>
  <default class="table-contents" :logoHeader="logoHeader">
    <div class="flex items-center">
      <div class="w-1/2 pl-6">
        <slot />
      </div>
      <div class="w-1/2 flex self-end justify-center">
        <img
          :src="tocImage"
          alt="new section"
          width="400"
          height="400"
          class="ml-auto object-cover max-h-[400px]"
        />
      </div>
    </div>
  </default>
</template>

<script setup lang="ts">
import Default from "../layouts/default.vue";

const props = defineProps({
  gradientColors: {
    type: Array,
    default: () => ["#A21CAF", "#5B21B6"],
  },
  tocImage: {
    type: String,
    default: "./theme/images/section-illustration.svg",
  },
});
</script>
