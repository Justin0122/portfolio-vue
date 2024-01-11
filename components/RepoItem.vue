<template>
  <div
      class="repo-card p-4 rounded-md mb-4 shadow-md hover:shadow-lg transition-all duration-500 ease-in-out dark:hover:bg-gray-800 bg-opacity-20 bg-gray-900 hover:bg-opacity-100 dark:hover:text-white cursor-default flex flex-col relative hover:bg-green-400 hover:scale-105 transform hover:text-gray-900 min-h-48 hover:shadow-green-400"
      :class="{'bg-gray-100 dark:bg-gray-900': repo.name === 'Error fetching repositories'}">
    <div>
      <a :href="repo.repo_url" target="_blank" class="text-lg font-bold hover:underline">{{ repo.name }}</a>
      <div class="dates text-gray-500 text-sm float-right flex flex-col">
        <span class="text-gray-800 dark:text-gray-400 text-sm">Updated {{ formatDate(repo.updated_at) }}</span>
      </div>
    </div>
    <p class="text-base">{{ repo.description }}</p>
    <div class="languages flex flex-row flex-wrap mt-auto">
        <span v-for="(value, key) in repo.languages" :key="key"
              :class="`text-xs dark:text-gray-800 rounded-full px-2 py-1 mr-1 mb-1 ${getLanguageColor(key)}`">
          {{ key }}
          {{ toPercentage(value) }}%
        </span>
    </div>
  </div>
</template>

<script setup>
import {defineProps} from 'vue';
import moment from 'moment';

const props = defineProps({
  repo: Object,
});

const repo = props.repo;
const formatDate = (dateString) => moment(dateString).fromNow();

const totalSize = Object.values(repo.languages).reduce((a, b) => a + b, 0);
const toPercentage = (value) => ((value / totalSize) * 100).toFixed(2);

function getLanguageColor(language) {
  const colors = {
    JavaScript: 'bg-yellow-500',
    HTML: 'bg-orange-500',
    CSS: 'bg-blue-500',
    SCSS: 'bg-pink-600',
    PHP: 'bg-indigo-400',
    Blade: 'bg-red-500',
    Python: 'bg-yellow-600',
    EJS: 'bg-red-600',
    Vue: 'bg-green-500',
    TypeScript: 'bg-blue-600',
  };
  return colors[language] || 'bg-gray-500';
}

</script>

<style scoped>

.repo-card:hover {
  background-color: rgba(186, 127, 239, 0.77);
  background-image: radial-gradient(at 100% 100%, rgba(78, 234, 185, 0.76) 0, transparent 67%), radial-gradient(at 16% 19%, rgba(155, 106, 234, 0.77) 0, transparent 85%);
  background-position: center center;
  -webkit-box-shadow: 8px 11px 21px -3px rgba(102, 255, 125, 1);
  -moz-box-shadow: 8px 11px 21px -3px rgba(102, 255, 125, 1);
  box-shadow: 8px 11px 21px -3px rgba(102, 255, 125, 1);
}

@media (prefers-color-scheme: dark) {
  .repo-card:hover {
    background-color: rgba(147, 51, 234, 0.77);
    background-image: radial-gradient(at 100% 100%, rgba(5, 150, 105, 0.76) 0, transparent 67%), radial-gradient(at 16% 19%, rgba(91, 33, 182, 0.77) 0, transparent 85%);
    background-position: center center;
    background-repeat: no-repeat;
    -webkit-box-shadow: 8px 11px 21px -3px rgba(4, 114, 79, 0.76);
    -moz-box-shadow: 8px 11px 21px -3px rgba(4, 114, 79, 0.76);
    box-shadow: 8px 11px 21px -3px rgba(4, 114, 79, 0.76);
  }
}

</style>
