<script setup>
import { ref, computed, watch, onMounted, onBeforeUnmount } from 'vue';

const taskInput = ref(null); // Template ref untuk input
const tasks = ref([
  { id: 1, text: 'Belajar Vue 3', completed: false },
  { id: 2, text: 'Mengerjakan Final Project', completed: false }
]);

const newTask = ref('');
const message = ref(''); // Untuk menampilkan pesan watcher

// Computed: Hitung jumlah tugas yang selesai
const completedTasks = computed(() => tasks.value.filter(task => task.completed).length);
const totalTasks = computed(() => tasks.value.length);

// Watcher: Pantau perubahan dalam daftar tugas
watch(tasks, (newVal, oldVal) => {
  message.value = `Daftar tugas berubah! Sekarang ada ${newVal.length} tugas.`;
}, { deep: true });

// Tambah tugas baru
const addTask = () => {
  if (newTask.value.trim() !== '') {
    tasks.value.push({
      id: Date.now(),
      text: newTask.value,
      completed: false
    });
    newTask.value = '';
    taskInput.value.focus(); // Gunakan template ref untuk fokus ke input
  }
};

// Hapus tugas berdasarkan ID
const removeTask = (taskId) => {
  tasks.value = tasks.value.filter(task => task.id !== taskId);
};

// Lifecycle Hooks
onMounted(() => {
  console.log('✅ Aplikasi To-Do List dimulai!');
});

onBeforeUnmount(() => {
  console.log('🛑 Aplikasi To-Do List ditutup!');
});
</script>

<template>
  <div class="container">
    <h2>📋 To-Do List</h2>

    <!-- Input untuk menambah tugas -->
    <input ref="taskInput" v-model="newTask" placeholder="Tambahkan tugas..." @keyup.enter="addTask" />
    <button @click="addTask">Tambah</button>

    <p v-if="message" class="message">{{ message }}</p>

    <!-- List Rendering dengan v-for -->
    <ul>
      <li v-for="task in tasks" :key="task.id">
        <input type="checkbox" v-model="task.completed" />
        <span :class="{ completed: task.completed }">{{ task.text }}</span>
        <button class="delete-btn" @click="removeTask(task.id)">Hapus</button>
      </li>
    </ul>

    <!-- Menampilkan jumlah tugas yang selesai -->
    <p>✔️ {{ completedTasks }} dari {{ totalTasks }} tugas selesai</p>
  </div>
</template>