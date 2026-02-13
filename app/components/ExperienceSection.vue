<script setup lang="ts">
const experiences = ref([
  {
    title: 'Desarrollador Full Stack',
    company: 'Autónomo',
    period: '2021 - Actualidad',
    description:
      'Desarrollo de soluciones web personalizadas para clientes diversos. Gestión completa del ciclo de vida del proyecto desde el diseño hasta el deployment.',
    technologies: [
      { name: 'Vue.js', icon: 'i-simple-icons-vuedotjs' },
      { name: 'Nuxt.js', icon: 'i-simple-icons-nuxtdotjs' },
      { name: 'React.js', icon: 'i-simple-icons-react' },
      { name: '.NET', icon: 'i-simple-icons-dotNET' },
      { name: 'Node.js', icon: 'i-simple-icons-nodejs' },
      { name: 'Tailwind CSS', icon: 'i-simple-icons-tailwindcss' }
    ],
    achievements: [
      'Completé 10+ proyectos',
      'Aprendizaje continuo',
      'Desarrollé aplicaciones a la medida'
    ]
  },
  {
    title: 'Desarrollador .NET',
    company: 'Vitamédica',
    period: 'Septiembre 2023 - Agosto 2024',
    description:
      'Diseñé y desarrollé un servicio WCF para el módulo de estado de cuenta utilizando Arquitectura Limpia en C#, mejorando la mantenibilidad del código. Implementé interfaces dinámicas en ASP.NET integrando JavaScript, jQuery y Bootstrap para una mejor interacción del usuario. Optimicé la gestión de datos mediante el uso de SQL Server y procedimientos almacenados (Store Procedures) para asegurar la integridad y rapidez de las consultas.',
    technologies: [
      { name: '.NET', icon: 'i-simple-icons-dotNET' },
      { name: 'JavaScript', icon: 'i-simple-icons-javascript' },
      { name: 'jQuery', icon: 'i-simple-icons-jquery' },
      { name: 'Bootstrap', icon: 'i-simple-icons-bootstrap' },
      { name: 'SQL Server', icon: 'i-simple-icons-microsoftsqlserver' }
    ],
    achievements: [
      'Mejoré la calidad del código implementando Arquitectura Limpia',
      'Implementé interfaces dinámicas en ASP.NET para una mejor interacción del usuario',
      'Optimicé la gestión de datos mediante el uso de SQL Server y procedimientos almacenados'
    ]
  },
  {
    title: 'Soporte Técnico',
    company: 'Soluciones Tecnológicas GM',
    period: 'Enero 2019 - Junio 2023',
    description: 'Líder del área de soporte técnico',
    technologies: [
      { name: 'Windows', icon: 'i-simple-icons-windows' },
      { name: 'Linux', icon: 'i-simple-icons-linux' },
      { name: 'Chrome', icon: 'i-simple-icons-googlechrome' }
    ],
    achievements: [
      'Lideré el área de soporte técnico, gestionando el mantenimiento preventivo y correctivo de infraestructura tecnológica.',
      'Resolución de incidencias críticas de hardware y software, garantizando la continuidad operativa de los servicios.'
    ]
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
    id="experience"
    description="Mi trayectoria profesional y crecimiento en el mundo tecnológico"
  >
    <template #title>
      <h2 class="text-4xl font-light">
        Experiencia
        <span class="font-semibold text-blue-600 dark:text-blue-400">Laboral</span>
      </h2>
    </template>

    <div class="relative mx-auto max-w-4xl">
      <div
        class="absolute top-0 bottom-0 left-8 hidden w-px bg-linear-to-b from-blue-300 via-blue-200 to-transparent md:left-1/2 md:-translate-x-px dark:from-blue-700 dark:via-blue-600"
      ></div>

      <div class="space-y-12">
        <div
          v-for="(exp, index) in experiences"
          :key="index"
          class="scroll-reveal relative"
          :class="index % 2 === 0 ? 'md:pr-[50%]' : 'md:pl-[50%]'"
        >
          <div
            class="absolute top-8 left-8 z-10 flex h-4 w-4 items-center justify-center md:left-1/2 md:-translate-x-1/2"
          >
            <div
              class="h-4 w-4 rounded-full border-4 border-blue-100 bg-blue-500 dark:border-blue-900 dark:bg-blue-400"
            ></div>
          </div>

          <div class="ml-16 md:ml-0">
            <div
              class="card-hover group relative overflow-hidden rounded-2xl bg-white p-6 shadow-lg shadow-zinc-200/50 dark:bg-zinc-900 dark:shadow-zinc-800/50"
            >
              <div
                class="absolute inset-0 -translate-x-full bg-linear-to-r from-blue-50 to-transparent opacity-0 transition-all duration-500 group-hover:translate-x-0 dark:from-blue-900/20"
              ></div>

              <div class="relative z-10">
                <div class="mb-4 flex flex-wrap items-start justify-between gap-2">
                  <div>
                    <h3 class="text-xl font-bold text-zinc-800 dark:text-zinc-200">
                      {{ exp.title }}
                    </h3>
                    <div class="mt-1 flex flex-wrap items-center gap-2">
                      <p class="font-medium text-blue-600 dark:text-blue-400">
                        {{ exp.company }}
                      </p>
                      <span class="text-zinc-300 dark:text-zinc-600">•</span>
                      <UBadge variant="subtle" color="neutral" size="sm">
                        {{ exp.period }}
                      </UBadge>
                    </div>
                  </div>
                </div>

                <p class="mb-5 leading-relaxed text-zinc-600 dark:text-zinc-400">
                  {{ exp.description }}
                </p>

                <div class="mb-5">
                  <h4
                    class="mb-3 flex items-center gap-2 font-semibold text-zinc-800 dark:text-zinc-300"
                  >
                    <UIcon name="i-heroicons-trophy" class="text-blue-500" />
                    Logros destacados
                  </h4>
                  <ul class="space-y-2">
                    <li
                      v-for="achievement in exp.achievements"
                      :key="achievement"
                      class="flex items-start gap-3 text-sm text-zinc-600 dark:text-zinc-400"
                    >
                      <UIcon
                        name="i-heroicons-check-circle"
                        class="mt-0.5 shrink-0 text-blue-500"
                      />
                      <span>{{ achievement }}</span>
                    </li>
                  </ul>
                </div>

                <div>
                  <h4
                    class="mb-3 flex items-center gap-2 font-semibold text-zinc-800 dark:text-zinc-300"
                  >
                    <UIcon name="i-heroicons-code-bracket-square" class="text-blue-500" />
                    Tecnologías
                  </h4>
                  <div class="flex flex-wrap gap-2">
                    <UBadge
                      v-for="tech in exp.technologies"
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
            </div>
          </div>
        </div>
      </div>
    </div>
  </UPageSection>
</template>
