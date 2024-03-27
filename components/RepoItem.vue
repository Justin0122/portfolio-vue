<template>
  <a id="glitch"
     :class="{'bg-gray-100 dark:bg-gray-900': repo.name === 'Error fetching repositories'}"
     :href="repo.repo_url"
      class="repo-card rounded-md mb-4 shadow-md hover:shadow-lg transition-all duration-500 ease-in-out dark:hover:bg-gray-800 bg-opacity-20 bg-red-900 hover:bg-opacity-100 dark:hover:text-cyan-300 flex flex-col relative hover:bg-green-400 transform hover:text-gray-900 min-h-48 border-red-800 border-2 hover:border-red-800"
     target="_blank">
    <div>
      <div>

        <div id="glitch-text" :data-text="glitchText(repo.name)"
           class="text-lg font-bold transition-all duration-500 ease-in-out">
         <h3  :class="addGlitchEffect()"
            class="ml-3  mr-1 text-lg font-bold transition-all duration-500 ease-in-out">{{ repo.name }}</h3>
        </div>
      </div>
      <div class="dates text-gray-500 text-sm float-left pl-4 flex flex-col">
        <span class="text-gray-800 dark:text-gray-400 text-sm mr-4">Updated {{ formatDate(repo.updated_at) }}</span>
      </div>
    </div>
    <p class="p-4 text-base text-yellow-500 mt-7">{{ repo.description }}</p>
    <div class="languages flex flex-row flex-wrap mt-auto ml-2">
<span v-for="(value, key) in repo.languages" :key="key"
      class="inline-block rounded-s px-2 py-1 text-md font-bold mr-2 mb-2 relative group border border-yellow-400">
  <i v-if="deviconExists(key)" :class="`devicon-${getDisplayName(key).toLowerCase()}-plain colored text-white`"></i>
  <span v-else class="text-white"> {{ key }}</span>
  {{ toPercentage(value) }}%
  <span
      class="hidden group-hover:inline-block absolute bottom-full left-1/2 transform ml-2 -translate-x-1/2 bg-black bg-opacity-75 text-white px-2 py-1 text-xs font-bold rounded whitespace-nowrap">
    {{ key }} {{ toPercentage(value) }}%
  </span>
</span>
    </div>
  </a>
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

const languageData = {
  JavaScript: {devicon: true, displayName: 'JavaScript'},
  HTML: {devicon: true, displayName: 'HTML'},
  CSS: {devicon: true, displayName: 'CSS3'},
  SCSS: {devicon: true, displayName: 'SASS'},
  PHP: {devicon: true, displayName: 'PHP'},
  Laravel: {devicon: true, displayName: 'Laravel'},
  Python: {devicon: true, displayName: 'Python'},
  VueJS: {devicon: true, displayName: 'VueJS'},
  TypeScript: {devicon: true, displayName: 'TypeScript'},
  Shell: {devicon: true, displayName: 'Bash'},
  Blade: {devicon: true, displayName: 'Laravel'},
};

function getDisplayName(language) {
  return languageData[language]?.displayName || language;
}

function getLanguageColor(language) {
  if (language === 'Vue') language = 'VueJS';
  if (language === 'Blade') language = 'Laravel';
  if (language === 'CSS') language = 'CSS3';
  return languageData[language]?.color || 'bg-gray-500';
}

function deviconExists(language) {
  if (language === 'Vue') language = 'VueJS';
  if (language === 'Blade') language = 'Laravel';
  return languageData[language]?.devicon || false;
}

function glitchText(text) {
  const chance = 0.1;
  const letters = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
  let result = '';
  for (const char of text) {
    result += Math.random() < chance ? letters.charAt(Math.floor(Math.random() * letters.length)) : char;
  }
  return result;
}

function addGlitchEffect() {
  return Math.random() < 0.1 ? 'cyberpunk glitched' : 'cyberpunk';
}

</script>

<style lang="scss">
.repo-card:hover {
  background-color: rgba(186, 127, 239, 0.77);
  background-image: radial-gradient(at 100% 100%, rgba(255, 34, 127, 0.76) 0, transparent 67%), radial-gradient(at 16% 19%, rgba(155, 106, 234, 0.77) 0, transparent 85%);
  background-position: center center;
  -webkit-box-shadow: 8px 11px 21px -3px rgba(102, 255, 125, 1);
  -moz-box-shadow: 8px 11px 21px -3px rgba(102, 255, 125, 1);
  box-shadow: 8px 11px 21px -3px rgba(102, 255, 125, 1);
}

@media (prefers-color-scheme: dark) {
  .repo-card:hover {
    background-color: rgb(97, 28, 32);
    background-image: radial-gradient(at 100% 100%, rgba(150, 5, 44, 0.76) 0, transparent 67%), radial-gradient(at 16% 19%, rgb(97, 28, 32) 0, transparent 85%);
    background-position: center center;
    background-repeat: no-repeat;
    -webkit-box-shadow: 8px 11px 21px -3px rgba(244, 224, 0, 0.76);
    -moz-box-shadow: 8px 11px 21px -3px rgba(255, 224, 26, 0.76);
    box-shadow: 8px 11px 21px -3px rgba(255, 235, 107, 0.76);
  }

  .repo-card:hover #glitch-text {
    position: relative;
  }

  #glitch-text::before,
  #glitch-text::after {
    animation-iteration-count: infinite;
    animation-timing-function: linear;
    animation-direction: alternate-reverse;
    overflow: hidden;
    position: absolute;
    top: 0;
    clip: rect(0, 900px, 0, 0);
    border: 1px solid var(--colors-primary--600);
    clip-path: var(--ui-notch-path);
    padding-right: 0.5rem;
    content: attr(data-text);
  }
  .repo-card:hover #glitch-text::after {
    animation-name: glitch-animation;
    animation-duration: 4s;
    left: 4px;
    text-shadow: -1px 0 #ffa800;
  }
  .repo-card:hover #glitch-text::before {
    animation-name: glitch-animation-2;
    animation-duration: 6s;
    width: var(--ui-notch-hypotenuse);
    left: -4px;
    text-shadow: 1px 0 #00d8ff;
  }
}

</style>
