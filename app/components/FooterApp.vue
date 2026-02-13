<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const items: NavigationMenuItem[] = [
  {
    label: 'Sobre Mí',
    to: '#about'
  },
  {
    label: 'Skills',
    to: '#skills'
  },
  {
    label: 'Proyectos',
    to: '#projects'
  }
]
const currentYear = new Date().getFullYear()
</script>

<template>
  <UFooter
    :ui="{
      container: 'flex flex-col-reverse gap-2 items-start lg:flex-row'
    }"
  >
    <template #left>
      <div class="flex flex-col gap-2">
        <h4 class="text-primary text-xl font-bold">Gustavo González</h4>
        <p class="text-muted lg:w-120">
          Desarrollador full stack apasionado por crear soluciones tecnológicas que generen un
          impacto real.
        </p>
        <div class="flex gap-3" style="transition: all 0.8s cubic-bezier(0.16, 1, 0.3, 1) 0.5s">
          <UButton
            to="https://github.com/Gustavo-Glz"
            icon="i-simple-icons-github"
            size="lg"
            color="neutral"
            variant="ghost"
            target="_blank"
            aria-label="GitHub"
            class="cursor-pointer hover:bg-zinc-100 dark:hover:bg-zinc-800"
          ></UButton>
          <UButton
            to="https://www.linkedin.com/in/gustavo-gonz%C3%A1lez-montalvo-7aa92a228/"
            icon="i-simple-icons-linkedin"
            size="lg"
            color="neutral"
            variant="ghost"
            target="_blank"
            aria-label="LinkedIn"
            class="cursor-pointer hover:bg-zinc-100 dark:hover:bg-zinc-800"
          ></UButton>
          <UButton
            to="mailto:gustavo.gonzalez.montalvo@gmail.com"
            icon="i-heroicons-envelope"
            size="lg"
            color="neutral"
            variant="ghost"
            target="_blank"
            aria-label="Email"
            class="cursor-pointer hover:bg-zinc-100 dark:hover:bg-zinc-800"
          ></UButton>
        </div>
      </div>
    </template>
    <template #default>
      <div class="flex flex-col gap-2">
        <h4 class="text-highlighted font-semibold">Enlaces rapidos</h4>
        <UNavigationMenu :items="items" orientation="vertical" />
      </div>
    </template>
    <template #right>
      <div class="flex flex-col gap-2">
        <h4 class="text-highlighted font-semibold">Contacto</h4>
        <div class="flex flex-col gap-3">
          <span class="text-muted truncate text-sm">gustavo.gonzalez.montalvo@gmail.com</span>
          <span class="text-muted truncate text-sm">+52 238 103 8825</span>
          <span class="text-muted truncate text-sm">Puebla, México</span>
        </div>
      </div>
    </template>
  </UFooter>
  <UContainer>
    <USeparator />
    <div class="text-muted py-4 text-center text-sm">
      &copy; {{ currentYear }} Gustavo González. Todos los derechos reservados.
    </div>
  </UContainer>
</template>
