<script setup lang="ts">
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
