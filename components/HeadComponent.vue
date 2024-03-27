<script lang="ts" setup>
import { FULL_NAME, PROFILE_PIC_URL } from '~/config.js';
const name = FULL_NAME;
const profilePicUrl = PROFILE_PIC_URL;

useHead({
  title: name + ' - Portfolio',
  meta: [
    { name: 'description', content: `Hi! I'm ${name}, a full stack developer from the Netherlands. Check out my portfolio!` },
    { name: 'og:title', content: `${name} - Portfolio` },
    { name: 'og:description', content: `Hi! I'm ${name}, a full stack developer from the Netherlands. Check out my portfolio!` },
    { name: 'og:image', content: `${profilePicUrl}` },
    { name: 'og:image:alt', content: `${name} - Portfolio` },
    { name: 'og:url', content: `https://${name.split(' ').join('').toLowerCase()}.nl` },
    { name: 'og:site_name', content: `${name} - Portfolio` },
    { name: 'twitter:card', content: 'summary_large_image' },
    { name: 'twitter:site', content: '@justinjongstra' },
    { name: 'twitter:creator', content: '@justinjongstra' },
    { name: 'twitter:title', content: `${name} - Portfolio` },
    { name: 'twitter:description', content: `Hi! I'm ${name}, a full stack developer from the Netherlands. Check out my portfolio!` },
    { name: 'twitter:image', content: `${profilePicUrl}` },
    { name: 'twitter:image:alt', content: `${name} - Portfolio` }
  ],
  link: [
    { rel: 'icon', type: 'image/x-icon', href: PROFILE_PIC_URL }
  ],
})
</script>