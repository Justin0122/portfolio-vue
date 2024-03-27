<template>
  <div id="footerLinks" class="flex flex-row justify-center items-center">
    <div v-for="(link, index) in links" :key="index">
      <a :href="link.url" target="_blank">
        <img :alt="link.name" :src="`svg/${link.name.toLowerCase()}.svg`" class="w-8 h-8 mx-2"/>
      </a>
    </div>
  </div>
</template>

<script setup>
const links = [
  {
    name: 'Github',
    url: 'https://github.com/Justin0122/',
  },
  {
    name: 'LinkedIn',
    url: 'https://www.linkedin.com/in/justin-jongstra-11b873207/',
  },
  {
    name: 'Packagist',
    url: 'https://packagist.org/users/Justin0122/',
  },
  {
    name: 'Npm',
    url: 'https://www.npmjs.com/~justin0122',
  },
  {
    name: 'Mailto',
    url: 'mailto:justin@justinjongstra.nl',
  }
]
</script>