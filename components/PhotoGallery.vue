<template>
  <div>
    <h1>Photo Gallery</h1>
    <button @click="fetchData">Fetch data</button>
    <slot name="metrics" :count="numberOfPhotos"></slot>
    <ul>
      <li v-for="photo in photos" :key="photo.id">
        <NuxtLink :to="`/display/photos/${photo.id}`"><img :src="photo.thumbnailUrl" /></NuxtLink>
      </li>
    </ul>
  </div>
</template>
  
  <!-- <script>
  import { defineNuxtComponent } from '#app';
  export default defineNuxtComponent({
    data() {
      return {
        photos: []
      };
    },
    methods: {
      async fetchData() {
        await fetch('https://jsonplaceholder.typicode.com/photos')
          .then(response => response.json())
          .then(json => { this.photos = json });
      }
    },
    computed: {
      numberOfPhotos() {
        return this.photos.length;
      }
    }
  })
  </script> -->
  
<script setup>
const props = defineProps(['type', 'parms']);
let photos = ref([]);
const numberOfPhotos = computed(() => {
  if (props.parms.completed == 'true') {
    return photos.value.length;
  } else {
    return 0;
  }
});

async function fetchData() {
  await useAsyncData(() => {
    $fetch('https://jsonplaceholder.typicode.com/photos')
      .then(response => photos.value = response);
  }); // nuxt way of sending requests
}

</script>
  
<style scoped></style>