<template>
  <default class="intro">
    <div class="flex items-center">
      <figure class="w-1/2 px-12" v-if="introImage">
        <img
          :src="imageSrc"
          height="312"
          width="312"
          class="rounded-full p-0 bg-gradient-to-r from-orange-700 to-purple-800 dark:(from-white to-purple-50)"
        />
      </figure>
      <div :class="introImage ? 'w-1/2' : 'w-full'">
        <slot />
      </div>
    </div>
  </default>
</template>

<script setup lang="ts">
import { computed } from "vue";
import { resolveAssetUrl } from "../layoutHelper";
import Default from "../layouts/default.vue";

const props = defineProps({
  introImage: {
    type: String,
  },
});
const imageSrc = computed(() => resolveAssetUrl(props.introImage));
</script>
