<template>
  <div id="app"
       class="bg-gradient-to-b dark:from-black dark:via-purple-900 dark:to-black dark:text-gray-300 from-gray-100 via-purple-400 to-gray-100 text-gray-900 sm:bg-gradient-to-r sm:dark:from-black sm:dark:via-purple-900 sm:dark:to-black sm:dark:text-gray-300 sm:from-gray-100 sm:via-purple-400 sm:to-gray-100 sm:text-gray-900">

    <header class="header md:sticky top-0 bg-gray-900 shadow w-full py-4 px-6 bg-opacity-80 bg-blur z-10 relative">
      <nav class="flex items-center justify-between">
        <div class="text-2xl font-bold text-white dark:text-gray-300">{{ name }}</div>
        <Links/>
      </nav>
    </header>

    <Carousel/>

    <main class="max-w-6xl mx-auto py-2 sm:px-8 px-4 z-2">
      <section id="about" class="md:mb-24 mb-16 relative">
        <span class="text-3xl font-bold mb-4 text-gray-800 dark:text-gray-300">About Me</span>
        <div class="flex flex-col sm:flex-row space-y-4 sm:space-y-0 sm:space-x-4">
          <div class="w-full sm:w-1/3 px-4" style="position: relative; z-index: 2;">
            <img id="profilePicture" class="rounded-full mx-auto mb-4" :alt=name :src="avatar_url"/>
          </div>

          <div
              class="w-full sm:w-2/3 dark:bg-gray-900 dark:bg-opacity-80 bg-opacity-50 rounded-lg p-4 shadow bg-blur cursor-default bg-gray-100"
              id="aboutText">
            <p class="text-lg">
              <AboutMe />
            </p>
          </div>

        </div>
      </section>

      <section id="certificates">
        <h2 class="text-3xl font-bold mb-4">Certificates</h2>
        <div id="certificateList" class="grid sm:grid-cols-2 md:grid-cols-6 gap-4">
          <Certificates/>
        </div>
      </section>

      <template>
        <section id="repositories" class="mt-8">
          <h2 class="text-3xl font-bold mb-4">Repositories</h2>
          <div class="flex flex-col sm:flex-row space-y-4 sm:space-y-0 sm:space-x-4">
            <RepoItems/>
          </div>
        </section>
      </template>

      <section id="aspirations" class="mt-8">
        <Aspirations/>
      </section>

    </main>

    <footer>
      <Footer :name="name"/>
    </footer>

    <div id="modal">
      <!-- Modal content -->
    </div>
  </div>
  <HeadComponent />

</template>

<script>
import HeadComponent from "~/components/HeadComponent.vue";
import RepoItem from "~/components/RepoItems.vue";
import { FULL_NAME, PROFILE_PIC_URL } from '~/config.js';

export default {
  components: {RepoItem, HeadComponent},
  data() {
    return {
      name: FULL_NAME,
      avatar_url: PROFILE_PIC_URL,
    };
  },
};
</script>

<style>
/* Your CSS styles */
</style>
