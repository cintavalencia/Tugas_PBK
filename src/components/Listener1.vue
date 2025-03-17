<script setup>
import { ref } from 'vue';

const nama = ref (0);

const increment = () => {
    nama.value++;
}
</script>

<template>
    <div>
       <p>Jumlah klik: {{ nama }}</p>
       <button @click="increment">Klik saya</button>
    </div>
</template>