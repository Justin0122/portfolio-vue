<template>
  <div class="carousel-inner" id="carousel">
    <div v-for="(image, index) in images" :key="index">
      <div class="carousel-item" :class="{ active: index === 0 }">
<!--        <img :src="`${BASE_URL}/img/${image}`" alt="`Image-${index}`" />-->
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import { BASE_URL } from '~/config.js';

const images = ref([]);

onMounted(async () => {
  try {
    const response = await fetch(`${BASE_URL}/api/images`);
    images.value = await response.json();
  } catch (error) {
    console.error('Error fetching images:', error);
  }
});
</script>

<style scoped>
/* Your CSS styles */
</style>
