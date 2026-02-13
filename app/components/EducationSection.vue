<script setup lang="ts">
const education = ref([
  {
    type: 'formal',
    title: 'Licenciatura en Ingeniería en Sistemas Computacionales',
    institution: 'Instituto de Estudios Superiores del Estado de Puebla',
    period: '2009 - 2014',
    description:
      'Formación integral en desarrollo de software, arquitectura de sistemas, bases de datos y redes. Participación en proyectos académicos y actividades extracurriculares relacionadas con la tecnología.',
    achievements: [
      'Promedio: 8.0/10',
      'Proyecto: "Desarrollo de plataforma de evaluación de maestros"',
      'Participación en hackathons universitarios'
    ],
    technologies: [
      { name: '.NET', icon: 'simple-icons:dotnet' },
      { name: 'C#', icon: 'i-simple-icons-csharp' },
      { name: 'HTML', icon: 'i-simple-icons-html5' },
      { name: 'CSS', icon: 'i-simple-icons-css3' },
      { name: 'C++', icon: 'i-simple-icons-cplusplus' },
      { name: 'SQL', icon: 'i-simple-icons-mysql' }
    ]
  }
])

const continuousLearning = ref([
  {
    title: 'Vue.js: De cero a experto',
    platform: 'Udemy',
    period: '2023',
    description:
      'Aprende pinia, unit test, composition api, autenticación, composables, deployment, file structure, lazy load, vitest y más',
    instructor: 'Fernando Herrera',
    hours: '+37 horas',
    certificate: true,
    technologies: [
      { name: 'Vue.js', icon: 'i-simple-icons-vuedotjs' },
      { name: 'Vue Router', icon: 'i-simple-icons-vuedotjs' },
      { name: 'Pinia', icon: 'simple-icons:pinia' },
      { name: 'Vitest', icon: 'devicon-plain:vitest' }
    ]
  },
  {
    title: 'Aprende Programación Backend en C# .NET',
    platform: 'Udemy',
    period: '2023',
    description: 'Desarrollo de backend aprendiendo por medio de conceptos.',
    instructor: 'Héctor de León',
    hours: '+6 horas',
    certificate: true,
    technologies: [
      { name: '.NET', icon: 'simple-icons:dotnet' },
      { name: 'C#', icon: 'i-simple-icons-csharp' }
    ]
  },
  {
    title: 'Vue.js 3 - La Guía Completa - Composition Pinia MEVN 10 Apps',
    platform: 'Udemy',
    period: '2024',
    description:
      'Aprende Vue.js creando proyectos reales, aprende MEVN, pinia, composition, vue router, SFC, vuetify, firebase, composables APIs',
    instructor: 'Juan Pablo De la torre Valdez',
    hours: '+40 horas',
    certificate: true,
    technologies: [
      { name: 'Vue.js', icon: 'i-simple-icons-vuedotjs' },
      { name: 'Vue Router', icon: 'i-simple-icons-vuedotjs' },
      { name: 'Pinia', icon: 'simple-icons:pinia' },
      { name: 'Firebase', icon: 'i-simple-icons-firebase' },
      { name: 'Vuetify', icon: 'devicon-plain:vuetify' }
    ]
  },
  {
    title: 'TypeScript: Tu completa guía y manual de mano.',
    platform: 'DevTalles',
    period: '2024',
    description: 'La base sólida que necesitas para trabajar con TypeScript',
    instructor: 'Fernando Herrera',
    hours: '+8 horas',
    certificate: true,
    technologies: [
      { name: 'TypeScript', icon: 'i-simple-icons-typescript' },
      { name: 'JavaScript', icon: 'i-simple-icons-javascript' }
    ]
  }
])

const stats = ref([
  { value: '1', label: 'Grado Universitario', icon: 'i-heroicons-academic-cap' },
  { value: '4+', label: 'Cursos Completados', icon: 'i-heroicons-book-open' },
  { value: '130+', label: 'Horas de Formación', icon: 'i-heroicons-clock' }
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
    id="education"
    description="Mi formación académica y aprendizaje continuo en el mundo tecnológico"
  >
    <template #title>
      <h2 class="text-4xl font-light">
        Formación
        <span class="font-semibold text-blue-600 dark:text-blue-400">Académica</span>
      </h2>
    </template>

    <div class="mb-12">
      <h3 class="mb-6 flex items-center gap-2 text-2xl font-light text-zinc-700 dark:text-zinc-300">
        <UIcon name="i-heroicons-academic-cap" class="text-blue-500" />
        Estudios Formales
      </h3>

      <div
        v-if="education[0]"
        class="scroll-reveal card-hover group relative overflow-hidden rounded-2xl bg-white p-6 shadow-lg shadow-zinc-200/50 dark:bg-zinc-900 dark:shadow-zinc-800/50"
      >
        <div
          class="absolute inset-0 -translate-x-full bg-linear-to-r from-blue-50 to-transparent opacity-0 transition-all duration-500 group-hover:translate-x-0 dark:from-blue-900/20"
        ></div>

        <div class="relative z-10">
          <div class="mb-4 flex flex-wrap items-start justify-between gap-4">
            <div>
              <h4 class="text-xl font-bold text-zinc-800 dark:text-zinc-200">
                {{ education[0].title }}
              </h4>
              <div class="mt-1 flex flex-wrap items-center gap-2">
                <p class="font-medium text-blue-600 dark:text-blue-400">
                  {{ education[0].institution }}
                </p>
                <span class="text-zinc-300 dark:text-zinc-600">•</span>
                <UBadge variant="subtle" color="neutral">
                  {{ education[0].period }}
                </UBadge>
              </div>
            </div>
          </div>

          <p class="mb-5 leading-relaxed text-zinc-600 dark:text-zinc-400">
            {{ education[0].description }}
          </p>

          <div class="mb-5">
            <h4 class="mb-3 flex items-center gap-2 font-semibold text-zinc-800 dark:text-zinc-300">
              <UIcon name="i-heroicons-trophy" class="text-blue-500" />
              Logros académicos
            </h4>
            <ul class="space-y-2">
              <li
                v-for="achievement in education[0].achievements"
                :key="achievement"
                class="flex items-start gap-3 text-sm text-zinc-600 dark:text-zinc-400"
              >
                <UIcon name="i-heroicons-star" class="mt-0.5 shrink-0 text-blue-500" />
                <span>{{ achievement }}</span>
              </li>
            </ul>
          </div>

          <div>
            <h4 class="mb-3 flex items-center gap-2 font-semibold text-zinc-800 dark:text-zinc-300">
              <UIcon name="i-heroicons-code-bracket-square" class="text-blue-500" />
              Tecnologías estudiadas
            </h4>
            <div class="flex flex-wrap gap-2">
              <UBadge
                v-for="tech in education[0].technologies"
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

    <div>
      <h3 class="mb-6 flex items-center gap-2 text-2xl font-light text-zinc-700 dark:text-zinc-300">
        <UIcon name="i-heroicons-book-open" class="text-blue-500" />
        Aprendizaje Continuo
      </h3>

      <div class="grid grid-cols-1 gap-6 lg:grid-cols-2">
        <div
          v-for="(course, index) in continuousLearning"
          :key="course.title"
          class="scroll-reveal card-hover group relative overflow-hidden rounded-2xl bg-white p-6 shadow-lg shadow-zinc-200/50 dark:bg-zinc-900 dark:shadow-zinc-800/50"
          :style="{ transitionDelay: `${index * 100}ms` }"
        >
          <div
            class="absolute inset-0 -translate-x-full bg-linear-to-r from-blue-50 to-transparent opacity-0 transition-all duration-500 group-hover:translate-x-0 dark:from-blue-900/20"
          ></div>

          <div class="relative z-10">
            <div class="mb-3 flex flex-wrap items-start justify-between gap-2">
              <h4 class="font-semibold text-zinc-800 dark:text-zinc-200">
                {{ course.title }}
              </h4>
              <UBadge
                v-if="course.certificate"
                color="success"
                variant="subtle"
                size="sm"
                icon="i-heroicons-check-badge"
              >
                Certificado
              </UBadge>
            </div>

            <div class="mb-3 flex flex-wrap items-center gap-2 text-sm">
              <p class="font-medium text-blue-600 dark:text-blue-400">
                {{ course.platform }}
              </p>
              <span class="text-zinc-300 dark:text-zinc-600">•</span>
              <UBadge variant="subtle" color="neutral" size="sm">
                {{ course.period }}
              </UBadge>
            </div>

            <p class="mb-4 text-sm leading-relaxed text-zinc-600 dark:text-zinc-400">
              {{ course.description }}
            </p>

            <div class="mb-4 space-y-1 text-sm">
              <div class="flex items-center gap-2 text-zinc-600 dark:text-zinc-400">
                <UIcon name="i-heroicons-user" class="size-4" />
                <span
                  >Instructor:
                  <span class="font-medium text-zinc-800 dark:text-zinc-300">{{
                    course.instructor
                  }}</span></span
                >
              </div>
              <div class="flex items-center gap-2 text-zinc-600 dark:text-zinc-400">
                <UIcon name="i-heroicons-clock" class="size-4" />
                <span
                  >Duración:
                  <span class="font-medium text-zinc-800 dark:text-zinc-300">{{
                    course.hours
                  }}</span></span
                >
              </div>
            </div>

            <div class="flex flex-wrap gap-2">
              <UBadge
                v-for="tech in course.technologies"
                :key="tech.name"
                :icon="tech.icon"
                color="neutral"
                variant="subtle"
                size="sm"
              >
                {{ tech.name }}
              </UBadge>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="mt-16 grid grid-cols-1 gap-6 sm:grid-cols-3">
      <div
        v-for="(stat, index) in stats"
        :key="stat.label"
        class="scroll-reveal card-hover group relative overflow-hidden rounded-2xl bg-white p-6 text-center shadow-lg shadow-zinc-200/50 dark:bg-zinc-900 dark:shadow-zinc-800/50"
        :style="{ transitionDelay: `${index * 100}ms` }"
      >
        <div
          class="absolute inset-0 bg-linear-to-br from-blue-50 to-transparent opacity-0 transition-opacity duration-300 group-hover:opacity-100 dark:from-blue-900/20"
        ></div>

        <div class="relative z-10">
          <UIcon :name="stat.icon" class="mx-auto mb-2 size-7 text-blue-500" />
          <p class="text-3xl font-bold text-blue-600 dark:text-blue-400">
            {{ stat.value }}
          </p>
          <p class="text-sm text-zinc-600 dark:text-zinc-400">
            {{ stat.label }}
          </p>
        </div>
      </div>
    </div>
  </UPageSection>
</template>
