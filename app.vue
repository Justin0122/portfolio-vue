<template>
  <link href="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/devicon.min.css" rel="stylesheet">
  <div id="app"
       class="bg-gradient-to-b dark:from-black dark:via-red-900 dark:to-black dark:text-gray-300 from-gray-100 via-gray-400 to-gray-100 text-gray-900 sm:dark:from-red-900  sm:dark:to-gray-900 sm:from-gray-100 sm:via-red-400 sm:to-gray-100 sm:text-gray-900">
    <div class="scanline z-0"></div>

    <header id="header"
            class="header md:sticky top-0 bg-red-900 shadow w-full py-4 px-6 bg-opacity-80 bg-blur z-10 relative">
      <nav class="flex items-center justify-between">
        <div id="glitch-text-app" :data-text="glitchText(name)"
             class="text-2xl font-bold text-white dark:text-gray-300 flex flex-row items-center">
          {{ name }} <pre class="code"><span class="blink">█</span></pre>
        </div>
        <Links/>
      </nav>
    </header>

    <Carousel/>

    <main class="max-w-6xl mx-auto py-2 sm:px-8 px-4 z-2">
      <section id="about" class="md:mb-24 mb-16 relative">
        <h2 :class="addGlitchEffect()" class="text-3xl font-bold mb-4">About Me</h2>
        <div class="flex flex-col sm:flex-row space-y-4 sm:space-y-0 sm:space-x-4">
          <div class="w-full sm:w-1/3 px-4" style="position: relative; z-index: 2;">
            <img id="profilePicture" :alt=name :src="avatar_url" class="rounded-md mx-auto mb-4 border-2 border-yellow-300 hover:border-yellow-500 transition-all duration-500 ease-in-out dark:hover:border-yellow-400"/>
          </div>

          <div
              id="aboutText"
              class="w-full sm:w-2/3 dark:bg-gray-900 dark:bg-opacity-80 bg-opacity-50 rounded-lg p-4 shadow bg-blur cursor-default bg-gray-700 border-yellow-300 border-2 hover:border-yellow-500 transition-all duration-500 ease-in-out dark:hover:bg-gray-800 dark:hover:border-yellow-400 hover:drop-shadow-lg hover:shadow-lg hover:shadow-yellow-700">
            <p class="text-lg">
              <AboutMe/>
            </p>
          </div>

        </div>
      </section>

      <section id="certificates">
        <h2 :class="addGlitchEffect()" class="text-3xl font-bold mb-4">Certificates</h2>
        <div id="certificateList"
             class="w-full grid sm:grid-cols-2 md:grid-cols-6 gap-4 dark:bg-gray-900 dark:bg-opacity-80 bg-opacity-50 rounded-lg p-4 shadow bg-blur cursor-default bg-gray-700 border-yellow-300 border-2 hover:border-yellow-500 transition-all duration-500 ease-in-out dark:hover:bg-gray-800 dark:hover:border-yellow-400 hover:drop-shadow-lg hover:shadow-lg hover:shadow-yellow-700">
          <Certificates/>
        </div>
      </section>

      <template>
        <section id="repositories" class="mt-8">
          <h2 :class="addGlitchEffect()" class="text-3xl font-bold mb-4">Repositories</h2>
          <div
              class="flex flex-col sm:flex-row space-y-4 sm:space-y-0 sm:space-x-4 dark:bg-gray-900 dark:bg-opacity-80 bg-opacity-50 rounded-lg p-4 shadow bg-blur cursor-default bg-gray-700 border-yellow-300 border-2 hover:border-yellow-500 transition-all duration-500 ease-in-out dark:hover:border-yellow-400 hover:drop-shadow-lg hover:shadow-lg hover:shadow-yellow-700">
            <RepoItems/>
          </div>
        </section>
      </template>

      <section id="aspirations" class="my-8">
        <h2 :class="addGlitchEffect()" class="text-3xl font-bold mb-4">Aspirations</h2>
        <div
            class="w-full dark:bg-gray-900 dark:bg-opacity-80 bg-opacity-50 rounded-lg p-4 shadow bg-blur cursor-default bg-gray-700 border-yellow-300 border-2 hover:border-yellow-500 transition-all duration-500 ease-in-out dark:hover:bg-gray-800 dark:hover:border-yellow-400 hover:drop-shadow-lg hover:shadow-lg hover:shadow-yellow-700">
          <Aspirations/>
        </div>
      </section>
    </main>
    <footer>
      <Footer :name="name"/>
    </footer>
  </div>

  <HeadComponent/>

</template>

<script>
import HeadComponent from "~/components/HeadComponent.vue";
import RepoItem from "~/components/RepoItems.vue";
import {FULL_NAME, PROFILE_PIC_URL} from '~/config.js';

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

<script setup>
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
  return Math.random() < 0.2 ? 'cyberpunk glitched' : 'cyberpunk';
  }

</script>

<style lang="scss">
#app {
  --colors-bg--300: #1e181e;
  --colors-bg--500: #191a1e;
  --colors-primary--200: #f4908b;
  --colors-primary--300: #ea6f69;
  --colors-primary--500: #e8615a;
  --colors-primary--600: #9c3230;
  --colors-primary--700: #5e2122;
  --colors-primary--800: #451717;
  --colors-primary--900: #3c181a;
  --colors-secondary--500: #2be4ea;
  --colors-secondary--900: #295459;
  --colors-tertiary--500: #fed33f;
  --colors-on_bg--500: var(--colors-primary--500);
  --colors-on_tertiary--500: var(--colors-bg--300);
  --colors-on_primary--500: var(--colors-primary--200);
  --colors-active--500: #2bfea0;
  --fonts-primary: "Rajdhani", sans-serif;
  --fonts-secondary: "VT323", monospace;
  --ui-glow: 0 0 5px var(--colors-primary--500);
  --ui-glow-borders--500: 0 0 3px var(--colors-primary--500);
  --ui-glow-color: currentcolor;
  --ui-glow-text: -9px -6px 40px var(--ui-glow-color);
  --ui-glow-text--dimmed: -9px -6px 40px var(--ui-glow-color);
  --ui-elevation--1: 2px 2px 0 rgba(0, 0, 0, 0.8);
  --ui-notch-amount: 2rem;
  --ui-notch-hypotenuse: 22.627416px;
  --ui-notch-path: polygon(
          0 0,
          100% 0,
          100% calc(100% - var(--ui-notch-amount) + 2px),
          calc(100% - var(--ui-notch-amount) + 2px) 100%,
          0 100%
  );

  --ui-notch-path-reverse: polygon(
          100% 0,
          0 0,
          0 calc(100% - var(--ui-notch-amount) + 2px),
          calc(10% - var(--ui-notch-amount) + 2px) 100%,
          100% 100%
  );

  --glitched-duration: 0.9s;
  --glitched-long-duration: 3s;

  background-color: var(--colors-bg--500);
  background-image: radial-gradient(
          ellipse at 33% 10%,
          #461616 0%,
          transparent 75%
  );
  background-repeat: no-repeat;
  color: var(--colors-on_bg--500);
  font-family: var(--fonts-primary);
  font-size: 100%;
  line-height: 1.4;
  margin: 0;
  min-height: 100vh;
}

#header {
  justify-content: space-between;
  margin-bottom: 1rem;
}

#header::after {
  background-color: var(--colors-primary--500);
  box-shadow: var(--ui-glow);
  bottom: 0;
  content: "";
  height: 2px;
  position: absolute;
  left: 0;
  width: 100%;
}


@keyframes flicker {
  0% {
    box-shadow: 0 0 2px #ff0, 0 0 2px #ff0, 0 0 3px #ff0, 0 0 4px #ff0, 0 0 5px #ff0, 0 0 6px #ff0, 0 0 7px #ff0, 0 0 8px #ff0;
  }
  100% {
    box-shadow: 0 0 2px #ff0, 0 0 3px #ff0, 0 0 4px #ff0, 0 0 5px #ff0, 0 0 6px #ff0, 0 0 7px #ff0, 0 0 8px #ff0, 0 0 9px #ff0;
  }
}

#app {
  background: linear-gradient(183deg, rgba(141,35,46,0.5) 1%, rgba(141,35,46,0) 60%),
  linear-gradient(250deg, rgba(141,35,46,0) 21%, rgba(141,35,46,0.2) 20%, rgba(11,35,47,0.2) 50%),
  linear-gradient(250deg, rgba(141,35,46,0) 23%, rgba(141,35,46,0.2) 20%, rgba(11,35,47,0.2) 50%),
  linear-gradient(250deg, rgba(141,35,46,0) 25%, rgba(141,35,46,0.2) 20%, rgba(11,35,47,0.2) 50%),
  repeating-linear-gradient(179deg, rgba(255,255,255,0.1), rgba(255,255,255,0.1) 3px, rgba(0,0,0,0.1) 3px, rgba(0,0,0,0.1) 5px);;

  background-color: #0b232f;
  background-repeat: no-repeat;
  background-attachment: fixed;
}

@keyframes scanline {
  0.01% {
    height: 0;
  }
  99.99% {
    height: 100%
  }
  100% {
    height: 0;
  }
}

.scanline {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(255,255,255,0.02);
  animation: scanline 8s linear infinite;
  pointer-events: none;
}

@keyframes blink {
  0.01% {
    opacity: 0;
  }
  50% {
    opacity: 0;
  }
  50.01% {
    opacity: 1;
  }
}


#glitch:hover {
  animation: flicker 1s infinite;
}

#glitch {
  clip-path: var(--ui-notch-path);
}

#glitch-l {
  clip-path: var(--ui-notch-path-reverse);
}

@keyframes glitch-animation {
  0% {
    clip: rect(42px, 9999px, 44px, 0);
  }
  5% {
    clip: rect(12px, 9999px, 59px, 0);
  }
  10% {
    clip: rect(48px, 9999px, 29px, 0);
  }
  15% {
    clip: rect(42px, 9999px, 73px, 0);
  }
  20% {
    clip: rect(63px, 9999px, 27px, 0);
  }
  25% {
    clip: rect(34px, 9999px, 55px, 0);
  }
  30% {
    clip: rect(86px, 9999px, 73px, 0);
  }
  35% {
    clip: rect(20px, 9999px, 20px, 0);
  }
  40% {
    clip: rect(26px, 9999px, 60px, 0);
  }
  45% {
    clip: rect(25px, 9999px, 66px, 0);
  }
  50% {
    clip: rect(57px, 9999px, 98px, 0);
  }
  55% {
    clip: rect(5px, 9999px, 46px, 0);
  }
  60% {
    clip: rect(82px, 9999px, 31px, 0);
  }
  65% {
    clip: rect(54px, 9999px, 27px, 0);
  }
  70% {
    clip: rect(28px, 9999px, 99px, 0);
  }
  75% {
    clip: rect(45px, 9999px, 69px, 0);
  }
  80% {
    clip: rect(23px, 9999px, 85px, 0);
  }
  85% {
    clip: rect(54px, 9999px, 84px, 0);
  }
  90% {
    clip: rect(45px, 9999px, 47px, 0);
  }
  95% {
    clip: rect(37px, 9999px, 20px, 0);
  }
  100% {
    clip: rect(4px, 9999px, 91px, 0);
  }
}

@keyframes glitch-animation-2 {
  0% {
    clip: rect(65px, 9999px, 100px, 0);
  }
  5% {
    clip: rect(52px, 9999px, 74px, 0);
  }
  10% {
    clip: rect(79px, 9999px, 85px, 0);
  }
  15% {
    clip: rect(75px, 9999px, 5px, 0);
  }
  20% {
    clip: rect(67px, 9999px, 61px, 0);
  }
  25% {
    clip: rect(14px, 9999px, 79px, 0);
  }
  30% {
    clip: rect(1px, 9999px, 66px, 0);
  }
  35% {
    clip: rect(86px, 9999px, 30px, 0);
  }
  40% {
    clip: rect(23px, 9999px, 98px, 0);
  }
  45% {
    clip: rect(85px, 9999px, 72px, 0);
  }
  50% {
    clip: rect(71px, 9999px, 75px, 0);
  }
  55% {
    clip: rect(2px, 9999px, 48px, 0);
  }
  60% {
    clip: rect(30px, 9999px, 16px, 0);
  }
  65% {
    clip: rect(59px, 9999px, 50px, 0);
  }
  70% {
    clip: rect(41px, 9999px, 62px, 0);
  }
  75% {
    clip: rect(2px, 9999px, 82px, 0);
  }
  80% {
    clip: rect(47px, 9999px, 73px, 0);
  }
  85% {
    clip: rect(3px, 9999px, 27px, 0);
  }
  90% {
    clip: rect(26px, 9999px, 55px, 0);
  }
  95% {
    clip: rect(42px, 9999px, 97px, 0);
  }
  100% {
    clip: rect(38px, 9999px, 49px, 0);
  }
}
@media (min-width:801px){

.blink {
  opacity: 1;
  animation: blink 1s linear infinite;
}

#glitch-text-app::before,
#glitch-text-app::after {
  animation-iteration-count: infinite;
  animation-timing-function: linear;
  animation-direction: alternate-reverse;
  overflow: hidden;
  position: absolute;
  top: 14px;
  clip: rect(0, 900px, 0, 0);
  border: 1px solid var(--colors-primary--600);
  clip-path: var(--ui-notch-path);
  padding-right: 0.5rem;
  content: attr(data-text);
}

#glitch-text-app::after {
  animation-name: glitch-animation;
  animation-duration: 4s;
  left: 31px;
  text-shadow: -1px 0 #ffa800;
}

#glitch-text-app::before {
  animation-name: glitch-animation-2;
  animation-duration: 6s;
  width: var(--ui-notch-hypotenuse);
  left: 13px;
  text-shadow: 1px 0 #00d8ff;
  background: rgb(97, 28, 34);
}
}

h1.cyberpunk,
h2.cyberpunk,
h3.cyberpunk,
h4.cyberpunk {
  font-size: 2rem;
  line-height: 2.2rem;
  font-weight: 200;
  position: relative;
  padding-bottom: 15px;
}

h2.cyberpunk {
  font-size: 1.7rem;
  line-height: 1.9rem;
  font-weight: 300;
}

h3.cyberpunk {
  font-size: 1.4rem;
  line-height: 1.6rem;
  font-weight: 500;
}

h4.cyberpunk {
  font-size: 1rem;
  line-height: 1.2rem;
  font-weight: 700;
}

h1.cyberpunk:before,
h2.cyberpunk:before,
h3.cyberpunk:before,
h4.cyberpunk:before {
  content: "";
  display: block;
  position: absolute;
  bottom: 0px;
  left: 2px;
  width: 100%;
  height: 10px;
  background-color: #000;
  clip-path: polygon(0px 0px, 85px 0px, 90px 5px, 100% 5px, 100% 6px, 85px 6px, 80px 10px, 0px 10px);
}

h1.cyberpunk.glitched {
  animation-name: h1glitched;
  animation-duration: calc(var(--glitched-duration) * 1.4);
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

h2.cyberpunk.glitched {
  animation-name: h1glitched;
  animation-duration: calc(var(--glitched-duration) * 1.7);
  animation-iteration-count: infinite;
  animation-direction: reverse;
  animation-timing-function: linear;
}

h3.cyberpunk.glitched {
  animation-name: h1glitched;
  animation-duration: calc(var(--glitched-duration) * 1.1);
  animation-iteration-count: infinite;
  animation-direction: reverse;
  animation-timing-function: ease-out;
}

h4.cyberpunk.glitched {
  animation-name: h1glitched;
  animation-duration: calc(var(--glitched-duration) * 2.1);
  animation-iteration-count: infinite;
  animation-timing-function: ease-in-out;
}

@keyframes h1glitched {
  0% {
    transform: skew(-20deg);
    left: -4px;
  }
  10% {
    transform: skew(-20deg);
    left: -4px;
  }
  11% {
    transform: skew(0deg);
    left: 2px;
  }
  50% {
    transform: skew(0deg);
  }
  51% {
    transform: skew(10deg);
  }
  59% {
    transform: skew(10deg);
  }
  60% {
    transform: skew(0deg);
  }
  100% {
    transform: skew(0deg);
  }
}

h1.cyberpunk.glitched:before {
  animation-name: h1beforeglitched;
  animation-duration: calc(var(--glitched-duration) * 2);
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

@keyframes h1beforeglitched {
  0% {
    transform: skew(-20deg);
    left: -4px;
    clip-path: polygon(0px 0px, 85px 0px, 90px 5px, 100% 5px, 100% 6px, 85px 6px, 80px 10px, 0px 10px);
  }
  10% {
    transform: skew(-20deg);
    left: -4px;
    clip-path: polygon(0px 0px, 85px 0px, 90px 5px, 100% 5px, 100% 6px, 85px 6px, 80px 10px, 0px 10px);
  }
  11% {
    transform: skew(0deg);
    left: 2px;
    clip-path: polygon(0px 0px, 85px 0px, 90px 5px, 100% 5px, 100% 6px, 85px 6px, 80px 10px, 0px 10px);
  }
  50% {
    transform: skew(0deg);
    clip-path: polygon(0px 0px, 85px 0px, 90px 5px, 100% 5px, 100% 6px, 85px 6px, 80px 10px, 0px 10px);
  }
  51% {
    transform: skew(0deg);
    clip-path: polygon(0px 0px, 85px 0px, 90px 5px, 100% 5px, 40% 5px, calc(40% - 30px) 0px, calc(40% + 30px) 0px, calc(45% - 15px) 5px, 100% 5px, 100% 6px, calc(45% - 14px) 6px, calc(40% + 29px) 1px, calc(40% - 29px) 1px, calc(40% + 1px) 6px, 85px 6px, 80px 10px, 0px 10px);
  }
  59% {
    transform: skew(0deg);
    clip-path: polygon(0px 0px, 85px 0px, 90px 5px, 100% 5px, 40% 5px, calc(40% - 30px) 0px, calc(40% + 30px) 0px, calc(45% - 15px) 5px, 100% 5px, 100% 6px, calc(45% - 14px) 6px, calc(40% + 29px) 1px, calc(40% - 29px) 1px, calc(40% + 1px) 6px, 85px 6px, 80px 10px, 0px 10px);
  }
  60% {
    transform: skew(0deg);
    clip-path: polygon(0px 0px, 85px 0px, 90px 5px, 100% 5px, 100% 6px, 85px 6px, 80px 10px, 0px 10px);
  }
  100% {
    transform: skew(0deg);
    clip-path: polygon(0px 0px, 85px 0px, 90px 5px, 100% 5px, 100% 6px, 85px 6px, 80px 10px, 0px 10px);
  }
}

h2.cyberpunk:before {
  clip-path: polygon(0px 5px, 35px 5px, 40px 0px, 85px 0px, 90px 5px, 100% 5px, 100% 6px, 85px 6px, 80px 10px, 20px 10px, 15px 6px, 0px 6px);
}

h2.cyberpunk.glitched:before {
  animation-name: h2beforeglitched;
  animation-duration: calc(var(--glitched-duration) * 2);
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

@keyframes h2beforeglitched {
  0% {
    transform: scaleY(1);
  }
  10% {
    transform: scaleY(1);
  }
  11% {
    transform: scaleY(-1);
  }
  50% {
    transform: scaleY(-1);
  }
  51% {
    transform: scaleY(1);
  }
  59% {
    transform: scaleY(1);
  }
  60% {
    transform: scaleY(1);
  }
  100% {
    transform: scaleY(1);
  }
}

h3.cyberpunk:before {
  clip-path: polygon(0px 5px, 10px 5px, 15px 0px, 40px 0px, 45px 5px, 100% 5px, 100% 6px, 31px 6px, 27px 2px, 15px 2px, 8px 10px, 0px 10px);
}

h4.cyberpunk:before {
  clip-path: polygon(0px 3px, 15px 3px, 20px 0px, 80px 0px, 85px 3px, 100% 3px, 100% 4px, 85px 4px, 80px 7px, 20px 7px, 15px 4px, 0px 4px);
}

h1.cyberpunk:after,
h2.cyberpunk:after,
h3.cyberpunk:after,
h4.cyberpunk:after,
p.cyberpunk:after {
  content: "";
  animation-name: hxafter;
  animation-duration: var(--glitched-duration);
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

h3.cyberpunk:after,
h4.cyberpunk:after {
  animation-direction: reverse;
  animation-duration: calc(var(--glitched-duration) / 2);
}

@keyframes hxafter {
  0% {
    opacity: 0;
  }
  50% {
    opacity: 0;
  }
  51% {
    opacity: 1;
  }
  100% {
    opacity: 1;
  }
}

/* Separator */

hr {
  height: 14px;
  background-color: #000;
  width: 100%;
  clip-path: polygon(1px 0px, 0px 0px, 0px 0px, 8px 14px, 13px 14px, 22px 7px, 42px 6px, 49px 2px, 100% 2px, 100% 0px, 42px 0px, 35px 5px, 22px 6px, 13px 13px, 9px 13px);
  animation-name: hr;
  animation-duration: var(--glitched-long-duration);
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

@keyframes hr {
  0% {
    transform: skew(0deg);
  }
  15% {
    transform: skew(0deg);
  }
  16% {
    transform: skew(20deg);
  }
  20% {
    transform: skew(20deg);
  }
  21% {
    transform: skew(0deg);
  }
  100% {
    right: 35px;
  }
}

/* Scrollbar */

::-webkit-scrollbar {
  background-color: var(--yellow-color);
}
::-webkit-scrollbar-button {
  display: none;
}
::-webkit-scrollbar-track {
  display: none;
}
::-webkit-scrollbar-track-piece {
  display: none;
}
::-webkit-scrollbar-thumb {
  background-color: var(--red-color);
  border-bottom: 2px solid var(--border-color);
  border-right: 2px solid var(--border-color);
  transition: background var(--glitched-duration);
}
::-webkit-scrollbar-thumb:hover {
  background-color: var(--orange-color);
}
::-webkit-scrollbar-corner {
  display: none;
}
::-webkit-resizer {
  display: none;
}
</style>
