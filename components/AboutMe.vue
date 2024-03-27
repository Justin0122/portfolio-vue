<template>
  <div class="text-md text-yellow-500">
    Hello, I'm <span class="font-bold underline text-lg">Justin Jongstra</span>, a {{ age }}-year-old software developer
    from the Netherlands.
    <br><br>
    I'm currently pursuing my MBO (VET) Software Developer diploma at
    <a class="focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500 underline hover:no-underline"
       href="https://www.rijnijssel.nl/">
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
    const stats = extractStatsFromReadme(readme);

    document.getElementById('stats').innerHTML = stats.map(stat => {
      const [, alt, src] = stat.match(/!\[([^\]]+)\]\(([^\)]+)\)/);
      return `<img class="pt-2" src="${src}" alt="${alt}" />`;
    }).join('');
  } catch (error) {
    console.error('Error fetching README:', error);
  }
});

function extractStatsFromReadme(readme) {
  const start = readme.indexOf('## GitHub Stats');
  const end = readme.indexOf('Last update:', start);
  const statsSection = readme.slice(start, end).trim();
  return statsSection.split('\n').filter(stat => stat.includes('!['));
}
</script>

<style scoped>
/* Your CSS here */
</style>
