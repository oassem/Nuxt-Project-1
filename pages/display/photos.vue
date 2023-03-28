<template>
    <NuxtPage v-if="route.params.id"></NuxtPage>
    <PhotoGallery v-else :type="route.path.split('/')[2]" :parms="route.query">
        <template #metrics="slotProps">
            <p>Total photos count: {{ slotProps.count }}</p>
        </template>
    </PhotoGallery>
</template>
    
<script setup>
import { useRoute } from 'vue-router';
const route = useRoute();
</script>
    
<style scoped></style>
    