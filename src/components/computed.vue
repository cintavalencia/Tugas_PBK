<script setup>
import { ref, computed } from "vue";

const price = ref(0);
const discount = ref(0); // Diskon default 10%

// Menghitung harga setelah diskon menggunakan computed
const discountedPrice = computed(() => {
    return price.value - (price.value * discount.value) / 100;
});
</script>

<template>
  <div class="container">
    <h2>Hitung Harga Setelah Diskon</h2>
    <label>Harga Barang: </label>
    <input type="number" v-model="price" placeholder="Masukkan harga" />

    <label>Diskon (%): </label>
    <input type="number" v-model="discount" placeholder="Masukkan diskon" />

    <p>Harga setelah diskon: <strong>{{ discountedPrice }}</strong></p>
  </div>
</template>