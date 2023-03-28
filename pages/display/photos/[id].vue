<template>
    <h1>This is photo id: {{ id }}</h1>
</template>
 
<script setup>
import { useRoute } from 'vue-router';
const id = useRoute().params.id;
</script>
 
<style scoped></style>
 