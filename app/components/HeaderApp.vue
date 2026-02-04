<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const route = useRoute()

const items = computed<NavigationMenuItem[]>(() => [
  {
    label: 'Sobre Mí',
    to: '#about',
    active: route.path.startsWith('#about')
  },
  {
    label: 'Skills',
    to: '#skills',
    active: route.path.startsWith('#skills')
  },
  {
    label: 'Proyectos',
    to: '#projects',
    active: route.path.startsWith('#projects')
  },
  {
    label: 'Experiencia',
    to: '#experience',
    active: route.path.startsWith('#experience')
  },
  {
    label: 'Contacto',
    to: '#contact',
    active: route.path.startsWith('#contact')
  }
])
</script>

<template>
  <UHeader>
    <template #title>
      <UIcon name="simple-icons:dailydotdev" class="text-primary size-10" />
    </template>

    <UNavigationMenu :items="items" />

    <template #right>
      <UColorModeButton />
      <UButton to="#contact">Contactar</UButton>
    </template>

    <template #body>
      <UNavigationMenu :items="items" orientation="vertical" class="-mx-2.5" />
    </template>
  </UHeader>
</template>
