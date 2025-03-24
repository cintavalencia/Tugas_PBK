<script setup>
import { ref, watch } from 'vue';

const counter = ref(0);
const message = ref('');
const isMultipleOfFive = ref(false); // Menyimpan status kelipatan 5

watch(counter, (newValue, oldValue) => {
  if (newValue !== 0 && newValue % 5 === 0) {
    message.value = `Counter mencapai ${newValue}, kelipatan 5!`;
    isMultipleOfFive.value = true; // Aktifkan warna hijau
  } else {
    message.value = `Counter berubah dari ${oldValue} ke ${newValue}`;
    isMultipleOfFive.value = false; // Kembali ke warna hitam
  }
});

const increment = () => {
  counter.value++;
};

const decrement = () => {
  if (counter.value > 0) {
    counter.value--;
  }
};
</script>

<template>
  <div class="container">
    <h2>Watcher Counter</h2>
    <p :class="{
      'multiple-of-five':kondisi, 
    }">
      Nilai Counter: {{ counter }}
    </p>
    <button @click="decrement">Kurangi</button>
    <button @click="increment">Tambah</button>
    <p v-if="message" :class="{'green-text': isMultipleOfFive}">
      {{ message }}
    </p>
  </div>
</template>