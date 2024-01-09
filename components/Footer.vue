<template>
  <div>
    <footer id="pageFooter"
            class="bg-gray-900 text-white py-6 text-center bottom-0 w-full bg-opacity-80 shadow bg-blur">
      <div class="flex flex-col sm:flex-row justify-center items-center md:hidden" id="footerLinks">
        <Links/>
      </div>
      <p>&copy;
        {{ name }} - All Rights Reserved.
      </p>
    </footer>
  </div>
</template>

<script>
  export default {
    name: "Footer",
    props: {
      name: String,
    },
  };
</script>