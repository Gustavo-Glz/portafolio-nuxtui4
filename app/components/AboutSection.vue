<script setup lang="ts">
const items = ref([
  {
    title: 'Clean Code',
    description: 'Código limpio, mantenible y escalable siguiendo las mejores prácticas.',
    icon: 'i-heroicons-code-bracket',
    color: 'emerald',
    bgClass: 'bg-emerald-100 dark:bg-emerald-900/40',
    textClass: 'text-emerald-600 dark:text-emerald-400',
    hoverClass: 'group-hover:bg-emerald-50 dark:group-hover:bg-emerald-900/20'
  },
  {
    title: 'Trabajo en equipo',
    description:
      'Colaboración efectiva en equipos multidisciplinarios para entregar soluciones tecnológicas innovadoras.',
    icon: 'i-heroicons-user-group',
    color: 'blue',
    bgClass: 'bg-blue-100 dark:bg-blue-900/40',
    textClass: 'text-blue-600 dark:text-blue-400',
    hoverClass: 'group-hover:bg-blue-50 dark:group-hover:bg-blue-900/20'
  },
  {
    title: 'Innovación constante',
    description: 'Siempre buscando nuevas formas de mejorar y optimizar soluciones tecnológicas.',
    icon: 'i-heroicons-light-bulb',
    color: 'amber',
    bgClass: 'bg-amber-100 dark:bg-amber-900/40',
    textClass: 'text-amber-600 dark:text-amber-400',
    hoverClass: 'group-hover:bg-amber-50 dark:group-hover:bg-amber-900/20'
  }
])

const technologies = ref([
  { name: 'TypeScript', icon: 'i-simple-icons-typescript' },
  { name: 'Node.js', icon: 'i-simple-icons-nodejs' },
  { name: 'React', icon: 'i-simple-icons-react' },
  { name: 'Vue.js', icon: 'i-simple-icons-vuedotjs' },
  { name: 'Nuxt.js', icon: 'i-simple-icons-nuxtdotjs' },
  { name: 'Tailwind CSS', icon: 'i-simple-icons-tailwindcss' },
  { name: '.NET', icon: 'i-simple-icons-dotNET' }
])

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible')
        }
      })
    },
    { threshold: 0.1 }
  )

  document.querySelectorAll('.scroll-reveal').forEach((el) => {
    observer.observe(el)
  })
})
</script>

<template>
  <UPageSection
    id="about"
    description="Conoce mi trayectoria profesional y mi pasión por el desarrollo"
  >
    <template #title>
      <h2 class="text-4xl font-light">
        Sobre <span class="font-semibold text-blue-600 dark:text-blue-400">Mí</span>
      </h2>
    </template>

    <div class="grid grid-cols-1 gap-8 lg:grid-cols-2 lg:items-stretch">
      <div
        class="scroll-reveal card-hover group relative overflow-hidden rounded-2xl bg-white p-8 shadow-lg shadow-zinc-200/50 lg:flex lg:flex-col dark:bg-zinc-900 dark:shadow-zinc-800/50"
      >
        <div
          class="absolute -top-20 -right-20 h-64 w-64 rounded-full bg-blue-100 opacity-50 transition-transform duration-500 group-hover:scale-150 dark:bg-blue-900/30"
        ></div>

        <div class="relative z-10">
          <h2 class="mb-6 text-xl font-semibold text-zinc-800 dark:text-zinc-200">
            +5 años creando experiencias digitales excepcionales
          </h2>

          <p class="mb-4 leading-relaxed text-zinc-600 dark:text-zinc-400">
            Soy un desarrollador full stack apasionado por crear soluciones tecnológicas que generen
            un impacto real. Mi experiencia abarca desde el desarrollo frontend con React y
            TypeScript hasta arquitecturas backend robustas con Node.js y bases de datos escalables.
          </p>

          <p class="mb-6 leading-relaxed text-zinc-600 dark:text-zinc-400">
            He tenido la oportunidad de trabajar en proyectos diversos, desde startups hasta
            empresas enterprise, siempre enfocado en entregar productos de alta calidad que superen
            las expectativas del cliente y mejoren la experiencia del usuario.
          </p>

          <div class="flex flex-wrap gap-2">
            <UBadge
              v-for="tech in technologies"
              :key="tech.name"
              :icon="tech.icon"
              color="neutral"
              variant="subtle"
            >
              {{ tech.name }}
            </UBadge>
          </div>
        </div>
      </div>

      <div class="flex flex-col gap-6 lg:flex-1 lg:justify-between">
        <div
          v-for="(item, index) in items"
          :key="item.title"
          class="scroll-reveal card-hover group relative overflow-hidden rounded-2xl bg-white p-6 shadow-lg shadow-zinc-200/50 transition-all duration-300 lg:flex-1 dark:bg-zinc-900 dark:shadow-zinc-800/50"
          :style="{ transitionDelay: `${index * 100}ms` }"
        >
          <div
            class="absolute inset-0 opacity-0 transition-opacity duration-300 group-hover:opacity-100"
            :class="item.hoverClass"
          ></div>

          <div class="relative z-10 flex gap-4">
            <div
              class="flex h-12 w-12 shrink-0 items-center justify-center rounded-xl transition-colors"
              :class="item.bgClass"
            >
              <UIcon :name="item.icon" class="size-6" :class="item.textClass" />
            </div>
            <div class="flex flex-col gap-2">
              <h2 class="font-semibold text-zinc-800 dark:text-zinc-200">
                {{ item.title }}
              </h2>
              <p class="text-sm text-zinc-600 dark:text-zinc-400">
                {{ item.description }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </UPageSection>
</template>
