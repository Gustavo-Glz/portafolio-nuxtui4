<script setup lang="ts">
useSeoMeta({
  title: 'Gustavo González - Desarrollador Full Stack',
  description:
    'Bienvenido a mi portafolio personal. Soy Gustavo González, un desarrollador Full Stack apasionado por crear soluciones innovadoras y eficientes.',
  ogTitle: 'Gustavo González - Desarrollador Full Stack',
  ogDescription:
    'Bienvenido a mi portafolio personal. Soy Gustavo González, un desarrollador Full Stack apasionado por crear soluciones innovadoras y eficientes.',
  ogType: 'website',
  ogUrl: 'https://gustavogonzalez.dev',
  ogImage: '/og-image.png',
  twitterCard: 'summary_large_image',
  twitterTitle: 'Gustavo González - Desarrollador Full Stack',
  twitterDescription:
    'Bienvenido a mi portafolio personal. Soy Gustavo González, un desarrollador Full Stack apasionado por crear soluciones innovadoras y eficientes.',
  twitterImage: '/og-image.png'
})

onBeforeMount(() => {
  if (window.location.hash) {
    history.replaceState(null, '', window.location.pathname)
  }
})
</script>

<template>
  <UApp>
    <HeaderApp />
    <UMain>
      <NuxtPage />
    </UMain>
    <FooterApp />
  </UApp>
</template>
