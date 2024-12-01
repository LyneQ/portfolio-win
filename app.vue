<script setup lang="ts">
// setting up meta tags and body classes
useHead({
  title: 'lyneq.tech',
  meta: [
    { name: 'description', content: 'portfolio make my myself for yourself' }
  ],
  bodyAttrs: {
    class: 'dark-theme'
  },
  script: [
    {
      src: 'https://kit.fontawesome.com/70805063d4.js',
      crossorigin: "anonymous",
      async: true,
      defer: true
    }
  ]
})
</script>
<template>
  <nuxt-layout>
    <NuxtPage/>
  </nuxt-layout>
</template>
<style lang="scss">
@use "~/assets/scss/reset.scss";
@use "~/assets/scss/base.scss";
</style>