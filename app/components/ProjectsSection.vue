<script setup lang="ts">
const projects = ref([
  {
    id: 1,
    title: 'Portafolio Personal',
    description:
      'Mi propio portafolio desarrollado con Nuxt.js, Tailwind CSS y Nuxt UI. Un showcase de mis habilidades y proyectos.',
    image:
      'https://images.unsplash.com/photo-1460925895917-afdab827c52f?w=800&auto=format&fit=crop&q=80',
    technologies: [
      { name: 'Nuxt.js', icon: 'i-simple-icons-nuxtdotjs' },
      { name: 'Tailwind', icon: 'i-simple-icons-tailwindcss' },
      { name: 'TypeScript', icon: 'i-simple-icons-typescript' },
      { name: 'Nuxt UI', icon: 'i-heroicons-square-3-stack-3d' }
    ],
    demoLink: '#',
    githubLink: 'https://github.com/Gustavo-Glz/portafolio-nuxtui4'
  },
  {
    id: 2,
    title: 'E-commerce Backend API',
    description:
      'API REST Full robusta para una plataforma de e-commerce, con autenticación, manejo de productos y pasarela de pagos.',
    image:
      'https://images.unsplash.com/photo-1557821552-17105176677c?w=800&auto=format&fit=crop&q=80',
    technologies: [
      { name: 'Node.js', icon: 'i-simple-icons-nodejs' },
      { name: 'Express', icon: 'i-simple-icons-express' },
      { name: 'MongoDB', icon: 'i-simple-icons-mongodb' },
      { name: 'JWT', icon: 'i-heroicons-key' }
    ],
    demoLink: '#',
    githubLink: '#'
  },
  {
    id: 3,
    title: 'Sistema de Gestión de Tareas',
    description:
      'Aplicación web para la gestión eficiente de tareas y proyectos en equipos pequeños a medianos.',
    image:
      'https://images.unsplash.com/photo-1611224923853-80b023f02d71?w=800&auto=format&fit=crop&q=80',
    technologies: [
      { name: 'React', icon: 'i-simple-icons-react' },
      { name: 'Redux', icon: 'i-simple-icons-redux' },
      { name: 'Firebase', icon: 'i-simple-icons-firebase' },
      { name: 'Material UI', icon: 'i-simple-icons-materialui' }
    ],
    demoLink: '#',
    githubLink: '#'
  }
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
    id="projects"
    description="Una selección de mis trabajos más recientes y desafiantes"
  >
    <template #title>
      <h2 class="text-4xl font-light">
        Proyectos
        <span class="font-semibold text-blue-600 dark:text-blue-400">Destacados</span>
      </h2>
    </template>

    <div class="grid grid-cols-1 gap-8 md:grid-cols-2 lg:grid-cols-3">
      <div
        v-for="(project, index) in projects"
        :key="project.id"
        class="scroll-reveal card-hover group relative overflow-hidden rounded-2xl bg-white shadow-lg shadow-zinc-200/50 dark:bg-zinc-900 dark:shadow-zinc-800/50"
        :style="{ transitionDelay: `${index * 100}ms` }"
      >
        <div class="relative h-56 overflow-hidden rounded-t-2xl bg-zinc-200 dark:bg-zinc-800">
          <img
            :src="project.image"
            :alt="project.title"
            class="h-full w-full object-cover transition-transform duration-700 group-hover:scale-110"
            loading="lazy"
          />
          <div
            class="absolute inset-0 bg-gradient-to-t from-zinc-900/80 via-zinc-900/20 to-transparent opacity-0 transition-opacity duration-300 group-hover:opacity-100"
          ></div>
          <div
            class="absolute right-0 bottom-0 left-0 flex translate-y-full justify-center gap-3 p-4 transition-transform duration-300 group-hover:translate-y-0"
          >
            <UButton
              size="sm"
              color="primary"
              icon="i-heroicons-arrow-top-right-on-square"
              :to="project.demoLink"
              target="_blank"
              class="cursor-pointer"
            >
              Demo
            </UButton>
            <UButton
              size="sm"
              variant="outline"
              color="neutral"
              icon="i-heroicons-code-bracket-square"
              :to="project.githubLink"
              target="_blank"
              class="cursor-pointer border-zinc-300 text-zinc-700 hover:bg-zinc-100 hover:text-zinc-900 dark:border-zinc-600 dark:text-zinc-300 dark:hover:bg-zinc-800 dark:hover:text-zinc-100"
            >
              Código
            </UButton>
          </div>
        </div>

        <div class="p-6">
          <h3
            class="mb-2 text-xl font-semibold text-zinc-800 transition-colors group-hover:text-blue-600 dark:text-zinc-200 dark:group-hover:text-blue-400"
          >
            {{ project.title }}
          </h3>
          <p class="mb-4 line-clamp-2 text-sm leading-relaxed text-zinc-600 dark:text-zinc-400">
            {{ project.description }}
          </p>
          <div class="flex flex-wrap gap-2">
            <UBadge
              v-for="tech in project.technologies"
              :key="tech.name"
              :icon="tech.icon"
              color="neutral"
              variant="subtle"
              size="sm"
              class="cursor-pointer transition-transform duration-200 hover:scale-110"
            >
              {{ tech.name }}
            </UBadge>
          </div>
        </div>
      </div>
    </div>
  </UPageSection>
</template>
