<template>
  <div class="flex flex-col justify-center items-center">
    <div v-for="(certificate, index) in certificates" :key="index">
      <a :href="certificate.url"
         class="rounded-lg bg-blur h-36 object-cover hover:opacity-90 transition duration-300 hover:scale-105 ease-in-out"
         rel="noopener noreferrer"
         target="_blank">
        <img
            :alt="certificate.name"
            :src="certificate.imgUrl"
            class="rounded-lg bg-blur h-36 object-cover hover:opacity-90 transition duration-300 hover:scale-105 ease-in-out">
      </a>
    </div>
  </div>

</template>
<script setup>
const certificates = [
  {
    name: 'MTA Security Fundamentals',
    url: 'https://www.credly.com/badges/fdc5df64-f420-4fbb-81fe-82b9814091d8/public_url',
    imgUrl: 'https://images.credly.com/size/340x340/images/3f36cda2-b4c2-46ba-a6d8-f11219631451/MTA-Security_Fundamentals-600x600.png'
  }
]
</script>