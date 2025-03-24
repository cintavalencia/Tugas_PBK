<script setup>
import { ref } from 'vue';

// Daftar item
const items = ref(['Apel', 'Jeruk', 'Mangga', 'Anggur']);

// Input untuk item baru
const newItem = ref('');

// Fungsi menambah item baru ke daftar
const addItem = () => {
  if (newItem.value.trim()) {
    items.value.push(newItem.value.trim());
    newItem.value = ''; // Reset input
  }
};
</script>

<template>
  <div>
    <h2>Daftar Buah</h2>
    <ul>
      <li v-for="(item, index) in items" :key="index">{{ item }}</li>
    </ul>
    <input v-model="newItem" placeholder="Tambahkan buah..." />
    <button @click="addItem">Tambah</button>
  </div>
</template>