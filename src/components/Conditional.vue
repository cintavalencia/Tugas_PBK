<script setup>
import { ref } from 'vue';

const isVisible = ref(true);

const toggleVisibility = () => {
    isVisible.value = !isVisible.value;
}
</script>

<template>
    <div>
       <button @click="toggleVisibility">Tampilkan/Sembunyikan</button>

       <!--Menggunakan v-if-->
       <p v-if="isVisible">Teks ini akan muncul atau hilang berdasarkan kondisi.</p>

       <!--Menggunakan v-show-->
       <p v-show="isVisible">Teks ini akan tetap ada di DOM tetapi hanya disembunyikan.</p>
    </div>
</template>