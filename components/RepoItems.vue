<template>
  <div class="items-center justify-center flex flex-col">
    <div class="grid sm:grid-cols-1 md:grid-cols-2 gap-4">
      <div v-for="(repo, index) in repos" :key="index">
        <RepoItem :repo="repo"/>
      </div>
      <div v-if="repos.length === 0">
        <p id="notFound" class="text-lg">Loading...</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import {onMounted, ref} from 'vue';
import RepoItem from "~/components/RepoItem.vue";
import { BASE_URL } from '~/config.js';

const repos = ref([]);

onMounted(async () => {
  try {
    const response = await fetch(`${BASE_URL}/api/repositories`);
    repos.value = await response.json();
  } catch (error) {
    console.error('Error fetching repositories:', error);
    document.getElementById('notFound').innerText = 'Error fetching repositories. Please come back later.';
  }
});
</script>

<style>
/* Your CSS styles */
</style>
