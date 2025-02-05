<template>
  <div
    class="slidev-layout w-full h-full"
    :style="{
      backgroundImage: `url(${image})`,
      backgroundRepeat: 'no-repeat',
      backgroundPosition: 'center center',
      backgroundSize: 'cover',
    }"
  >
    <default>
      <div
        style="
          background-color: rgba(255, 255, 255, 0.7);
          border-radius: 10px;
          padding: 20px;
        "
      >
        <slot />
      </div>
    </default>
  </div>
</template>

<script setup lang="ts">
import Default from "../layouts/default.vue";
defineProps({
  image: {
    type: String,
  },
});
</script>
