<script setup lang="ts">
const items = ref([
  {
    title: 'Clean Code',
    description: 'Código limpio, mantenible y escalable siguiendo las mejores prácticas.',
    icon: 'mdi-code-tags-check'
  },
  {
    title: 'Trabajo en equipo',
    description:
      'Colaboración efectiva en equipos multidisciplinarios para entregar soluciones tecnológicas innovadoras.',
    icon: 'mdi-account-group-outline'
  },
  {
    title: 'Innovación constante',
    description: 'Siempre buscando nuevas formas de mejorar y optimizar soluciones tecnológicas.',
    icon: 'mdi-lightbulb-on-outline'
  }
])

const tecnologies = ref([
  { name: 'TypeScript', icon: 'logos:typescript-icon-round' },
  { name: 'Node.js', icon: 'logos:nodejs-icon-alt' },
  { name: 'React', icon: 'logos:react' },
  { name: 'Vue.js', icon: 'logos:vue' },
  { name: 'Nuxt.js', icon: 'logos:nuxt-icon' },
  { name: 'Tailwind CSS', icon: 'logos:tailwindcss-icon' },
  { name: '.NET', icon: 'logos:dotnet' }
])
</script>
<template>
  <UPageSection
    id="about"
    description="Conoce mi trayectoria profesional y mi pasión por el desarrollo"
  >
    <template #title>
      <h2 class="text-4xl">Sobre <span class="text-primary">Mí</span></h2>
    </template>
    <div class="grid grid-cols-1 justify-between gap-8 lg:grid-cols-2">
      <UPageCard spotlight>
        <template #title>
          <h2 class="text-lg">+5 años creando experiencias digitales excepcionales</h2>
        </template>
        <template #description>
          <p class="my-6">
            Soy un desarrollador full stack apasionado por crear soluciones tecnológicas que generen
            un impacto real. Mi experiencia abarca desde el desarrollo frontend con React y
            TypeScript hasta arquitecturas backend robustas con Node.js y bases de datos escalables.
          </p>
          <p>
            He tenido la oportunidad de trabajar en proyectos diversos, desde startups hasta
            empresas enterprise, siempre enfocado en entregar productos de alta calidad que superen
            las expectativas del cliente y mejoren la experiencia del usuario.
          </p>
        </template>
        <div class="flex flex-wrap gap-2">
          <UBadge
            v-for="tech in tecnologies"
            :key="tech.name"
            :icon="tech.icon"
            color="neutral"
            variant="soft"
          >
            {{ tech.name }}
          </UBadge>
        </div>
      </UPageCard>
      <div class="flex flex-col gap-6">
        <UPageCard
          v-for="item in items"
          :key="item.title"
          spotlight
          class="ransition-transform duration-200 hover:scale-105"
        >
          <div class="flex gap-4">
            <UIcon :name="item.icon" class="text-primary size-10" />
            <div class="flex flex-col gap-2">
              <h2 class="text-highlighted font-bold">{{ item.title }}</h2>
              <p class="text-muted text-sm">{{ item.description }}</p>
            </div>
          </div>
        </UPageCard>
      </div>
    </div>
  </UPageSection>
</template>
