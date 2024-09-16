<template>
  <default class="center">
    <div class="flex flex-col items-center justify-center text-center">
      <slot />

      <div class="mt-5">
        <div v-if="countdownTimer > 0">
          <h3>Temps restant :</h3>
          <p
            :class="{
              'mt-5 text-7xl': countdownTimer > 10,
              'mt-10 text-9xl': countdownTimer <= 10,
            }"
            :style="{ color: timerColor }"
          >
            {{ formattedTime }}
          </p>
          <button
            v-if="!isCounting"
            @click="startCountdown"
            class="mt-5 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
          >
            Démarrer le compte à rebours
          </button>
        </div>
        <div v-else class="text-2xl">
          <p
            class="font-bold font-title bg-clip-text text-transparent bg-gradient-to-r from-red-700 to-orange-800"
          >
            Le compte à rebours est terminé.
          </p>
        </div>
      </div>
    </div>
  </default>
</template>

<script setup lang="ts">
import Default from "../layouts/default.vue";
import { ref, computed } from "vue";

const props = defineProps({
  timer: {
    type: Number,
    default: 60,
  },
});

const countdownTimer = ref(props.timer);
const isCounting = ref(false);

const timerColor = computed(() => {
  const percentage = countdownTimer.value / props.timer;
  const red = Math.floor(255 * (1 - percentage));
  const green = Math.floor(255 * percentage);
  return `rgb(${red},${green},0)`;
});

const formattedTime = computed(() => {
  const hours = String(Math.floor(countdownTimer.value / 3600)).padStart(
    2,
    "0"
  );
  const minutes = String(
    Math.floor((countdownTimer.value % 3600) / 60)
  ).padStart(2, "0");
  const seconds = String(countdownTimer.value % 60).padStart(2, "0");
  return countdownTimer.value > 10 ? `${hours}:${minutes}:${seconds}` : seconds;
});

const countdown = () => {
  if (countdownTimer.value > 0) {
    setTimeout(() => {
      countdownTimer.value--;
      countdown();
    }, 1000);
  } else {
    isCounting.value = false;
  }
};

const startCountdown = () => {
  if (!isCounting.value) {
    countdownTimer.value = props.timer;
    isCounting.value = true;
    countdown();
  }
};
</script>
