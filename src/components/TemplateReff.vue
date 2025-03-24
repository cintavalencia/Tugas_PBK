<script setup>
import { ref, onMounted, onBeforeMount, onUpdated } from 'vue';

const hours = ref(0);
const minutes = ref(0);
const seconds = ref(0);
const timer = ref(null);

const startTimer = () => {
  if (!timer.value) {
    timer.value = setInterval(() => {
      seconds.value++;
      if (seconds.value === 60) {
        seconds.value = 0;
        minutes.value++;
      }
      if (minutes.value === 60) {
        minutes.value = 0;
        hours.value++;
      }
    }, 1000);
  }
};

const pauseTimer = () => {
  clearInterval(timer.value);
  timer.value = null;
};

const resetTimer = () => {
  pauseTimer();
  hours.value = 0;
  minutes.value = 0;
  seconds.value = 0;
};

const formatTime = (value) => (value < 10 ? `0${value}` : value);

onBeforeMount(() => {
  console.log('Komponen akan segera dimuat, persiapan dilakukan!');
});

onMounted(() => {
  console.log('Komponen telah dimuat! Timer tidak akan otomatis mulai.');
});

onUpdated(() => {
  console.log(`Waktu diperbarui: ${formatTime(hours.value)}:${formatTime(minutes.value)}:${formatTime(seconds.value)}`);
});
</script>

<template>
  <div class="container">
    <h2>⏲ Timer</h2>
    <p class="timer-display">
      {{ formatTime(hours) }}:{{ formatTime(minutes) }}:{{ formatTime(seconds) }}
    </p>
    <button @click="startTimer">▶️ Start</button>
    <button @click="pauseTimer">⏸ Pause</button>
    <button @click="resetTimer">🔄 Reset</button>
  </div>
</template>