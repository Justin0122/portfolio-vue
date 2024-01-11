<template>
  <div class="dark:text-gray-300 text-gray-800 text-md">
    Hello, I'm <span class="font-bold underline text-lg">Justin Jongstra</span>, a {{ age }}-year-old software developer from the Netherlands.
    <br><br>
    I'm currently pursuing my MBO (VET) Software Developer diploma at
    <a href="https://www.rijnijssel.nl/"
       class="focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500 underline hover:no-underline">
      <span class="text-orange-500">Rijn</span><span class="text-purple-500">IJssel</span>
    </a>.
    I'm deeply passionate about technologies like Laravel, Livewire, and Tailwind CSS, and I'm always eager to expand my
    expertise in these areas.
    <br><br>
    Apart from coding, I enjoy mountain biking, drawing, and playing video games.
    <br><br>

    <span class="text-lg font-bold">My skills:</span>
    <br>
    <span class="text-lg font-light">Laravel, Livewire, Tailwind CSS, HTML, CSS, JavaScript, PHP, MySQL, Git, GitHub, Linux, Windows, and more.</span>

    <br><br>

    <span class="text-lg font-bold">Overall Language Distribution:</span>
    <div id="stats" class="flex flex-wrap space-x-2"></div>
    <div class="text-sm text-gray-500" id="lastUpdate"></div>
  </div>

</template>

<script setup>
import {onMounted} from 'vue';
import {BASE_URL} from '~/config.js';

const age = Math.floor((new Date() - new Date(2001, 11, 22)) / 3.15576e+10);

onMounted(async () => {
  try {
    const response = await fetch(`${BASE_URL}/api/readme`);
    const readme = await response.text();
    const stats = readme.slice(readme.indexOf('## GitHub Stats'), readme.indexOf('Last update:', readme.indexOf('## GitHub Stats'))).trim()
        .split('\n')
        .filter(stat => stat.includes('!['));

    document.getElementById('stats').innerHTML = stats.map(stat => {
      const regex = /!\[([^\]]+)\]\(([^\)]+)\)/g;
      const matches = regex.exec(stat);
      if (matches) {
        const [, alt, src] = matches;
        return `<img class="pt-2" src="${src}" alt="${alt}" />`;
      }
      return '';
    }).join('');
  } catch (error) {
    console.error('Error fetching README:', error);
  }

});

</script>

<style scoped>
/* Your CSS styles */
</style>
