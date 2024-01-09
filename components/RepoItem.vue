<template>
  <div
      class="repo-card p-4 rounded-md mb-4 shadow-md hover:shadow-lg transition-all duration-300 ease-in-out dark:hover:bg-gray-800 bg-opacity-20 bg-gray-900 hover:bg-opacity-100 dark:hover:text-white cursor-default flex flex-col relative hover:bg-gray-800 hover:scale-105 transform hover:text-white"
      :class="{'bg-gray-100 dark:bg-gray-900': repo.name === 'Error fetching repositories'}">
    <div>
      <a :href="repo.repo_url" target="_blank" class="text-lg font-bold hover:underline">{{ repo.name }}</a>
      <div class="dates text-gray-500 text-sm float-right flex flex-col">
        <span class="text-gray-500 text-sm">Updated {{ formatDate(repo.updated_at) }}</span>
      </div>
    </div>
    <p class="text-base">{{ repo.description }}</p>

  </div>
</template>

<script setup>
import {defineProps} from 'vue';
import moment from 'moment';

const props = defineProps({
  repo: Object,
});

// Format date function
const formatDate = (dateString) => moment(dateString).fromNow();
</script>

<style scoped>
/* Your CSS styles */
</style>
