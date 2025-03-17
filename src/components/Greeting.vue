<script setup>
import { ref } from 'vue';

const nama = ref ('Valen');
</script>

<template>
    <div>
        <h1>halo saya {{ nama }}</h1>
    </div>
</template>