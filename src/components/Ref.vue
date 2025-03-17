<script setup>
import { ref } from 'vue';

const count = ref(0);

const increment = () => {
  count.value++;
};
</script>

<template>
    <div>
        <p>Nilai count: {{ count }}</p>
        <button @click="increment">Tambah</button>
    </div>
</template>