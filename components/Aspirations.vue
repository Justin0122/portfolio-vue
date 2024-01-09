<template>
  <h2 class="text-3xl font-bold mb-4">Aspirations</h2>
  <div class="bg-white dark:bg-gray-800 rounded-lg shadow-md p-6 transition duration-300 ease-in-out transform hover:scale-105">
    <p class="text-gray-700 dark:text-gray-300 mb-4">
      I'm passionate about becoming a Full-Stack Laravel Developer. Currently, I'm focused on enhancing my
      skills in PHP, JavaScript, and C++, along with mastering Laravel, Livewire, and Tailwind CSS. I'm also
      exploring microcontrollers as a side interest.
      <br><br>
      My goal is to build innovative web applications that provide seamless user experiences and solve
      real-world problems.
      <br><br>
      If you have any exciting projects or opportunities, feel free to reach out! I'm eager to learn and grow
      in this dynamic field.
    </p>
  </div>
</template>
<script setup>
  import {defineProps} from 'vue';

  const props = defineProps({
    name: String,
  });
</script>