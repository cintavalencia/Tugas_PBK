<script setup>
import { ref } from 'vue';

const nama = ref ('Valen');
</script>

<template>
    <div>
        <label for="nama">Nama:</label>
        <input id="nama" v-model="nama" placeholder="Masukkan Nama:" />
        <p>Halo, {{ nama }}!</p>
    </div>
</template>