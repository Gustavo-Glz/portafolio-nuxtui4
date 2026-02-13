<script setup lang="ts">
const skills = ref([
  {
    title: 'Frontend',
    icon: 'i-heroicons-code-bracket-square',
    color: 'from-blue-500 to-cyan-500',
    bgGradient: 'group-hover:from-blue-500/10 group-hover:to-cyan-500/10',
    technologies: [
      { name: 'Vue.js', icon: 'i-simple-icons-vuedotjs' },
      { name: 'Nuxt.js', icon: 'i-simple-icons-nuxtdotjs' },
      { name: 'React', icon: 'i-simple-icons-react' },
      { name: 'TypeScript', icon: 'i-simple-icons-typescript' },
      { name: 'Tailwind CSS', icon: 'i-simple-icons-tailwindcss' },
      { name: 'Pinia', icon: 'i-heroicons-circle-stack' }
    ]
  },
  {
    title: 'Backend',
    icon: 'i-heroicons-server-stack',
    color: 'from-emerald-500 to-teal-500',
    bgGradient: 'group-hover:from-emerald-500/10 group-hover:to-teal-500/10',
    technologies: [
      { name: 'Node.js', icon: 'i-simple-icons-nodejs' },
      { name: 'C#', icon: 'i-simple-icons-csharp' },
      { name: 'NestJS', icon: 'i-simple-icons-nestjs' },
      { name: 'PostgreSQL', icon: 'i-simple-icons-postgresql' },
      { name: 'Docker', icon: 'i-simple-icons-docker' }
    ]
  },
  {
    title: 'Herramientas',
    icon: 'i-heroicons-wrench-screwdriver',
    color: 'from-amber-500 to-orange-500',
    bgGradient: 'group-hover:from-amber-500/10 group-hover:to-orange-500/10',
    technologies: [
      { name: 'Git', icon: 'i-simple-icons-git' },
      { name: 'Postman', icon: 'i-simple-icons-postman' },
      { name: 'Prettier', icon: 'i-simple-icons-prettier' },
      { name: 'ESLint', icon: 'i-simple-icons-eslint' },
      { name: 'VS Code', icon: 'i-simple-icons-visualstudiocode' },
      { name: 'VS', icon: 'i-simple-icons-visualstudio' }
    ]
  },
  {
    title: 'Aprendiendo',
    icon: 'i-heroicons-academic-cap',
    color: 'from-violet-500 to-purple-500',
    bgGradient: 'group-hover:from-violet-500/10 group-hover:to-purple-500/10',
    technologies: [
      { name: 'Figma', icon: 'i-simple-icons-figma' },
      { name: 'Next.js', icon: 'i-simple-icons-nextdotjs' },
      { name: 'Prisma', icon: 'i-simple-icons-prisma' },
      { name: 'Vitest', icon: 'i-simple-icons-vitest' }
    ]
  }
])

const stats = ref([
  { value: '5+', label: 'Años de experiencia', icon: 'i-heroicons-clock', color: 'text-blue-500' },
  {
    value: '10+',
    label: 'Proyectos completados',
    icon: 'i-heroicons-folder-check',
    color: 'text-emerald-500'
  },
  { value: '15+', label: 'Tecnologías', icon: 'i-heroicons-cpu-chip', color: 'text-violet-500' }
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
    id="skills"
    description="Tecnologías y herramientas que domino para crear soluciones completas"
  >
    <template #title>
      <h2 class="text-4xl font-light">
        Stack <span class="font-semibold text-blue-600 dark:text-blue-400">Tecnológico</span>
      </h2>
    </template>

    <div class="grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-4">
      <div
        v-for="(skill, index) in skills"
        :key="skill.title"
        class="scroll-reveal card-hover group relative overflow-hidden rounded-2xl bg-white p-6 shadow-lg shadow-zinc-200/50 dark:bg-zinc-900 dark:shadow-zinc-800/50"
        :style="{ transitionDelay: `${index * 100}ms` }"
      >
        <div
          class="absolute inset-0 bg-gradient-to-br opacity-0 transition-opacity duration-500"
          :class="skill.bgGradient"
        ></div>

        <div class="relative z-10">
          <div
            class="mb-4 flex h-14 w-14 items-center justify-center rounded-xl bg-zinc-100 transition-all duration-300 group-hover:scale-110 group-hover:bg-white dark:bg-zinc-800 dark:group-hover:bg-zinc-700"
          >
            <UIcon :name="skill.icon" class="size-7 text-blue-600 dark:text-blue-400" />
          </div>

          <h3 class="mb-4 text-lg font-semibold text-zinc-800 dark:text-zinc-200">
            {{ skill.title }}
          </h3>

          <div class="flex flex-wrap gap-2">
            <UBadge
              v-for="tech in skill.technologies"
              :key="tech.name"
              :icon="tech.icon"
              color="neutral"
              variant="subtle"
              class="cursor-pointer transition-transform duration-200 hover:scale-110"
            >
              {{ tech.name }}
            </UBadge>
          </div>
        </div>

        <div
          class="absolute -right-8 -bottom-8 h-32 w-32 rounded-full transition-transform duration-500 group-hover:scale-150"
          :class="skill.color.split(' ')[0].replace('from-', 'bg-')"
          style="opacity: 0.08"
        ></div>
      </div>
    </div>

    <div class="mt-16 grid grid-cols-1 gap-6 sm:grid-cols-3">
      <div
        v-for="(stat, index) in stats"
        :key="stat.label"
        class="scroll-reveal card-hover group relative overflow-hidden rounded-2xl bg-white p-8 text-center shadow-lg shadow-zinc-200/50 dark:bg-zinc-900 dark:shadow-zinc-800/50"
        :style="{ transitionDelay: `${index * 100}ms` }"
      >
        <div
          class="absolute inset-0 bg-gradient-to-br from-blue-50/0 to-transparent opacity-0 transition-opacity duration-300 group-hover:opacity-100 dark:from-blue-900/20"
        ></div>

        <div class="relative z-10">
          <UIcon :name="stat.icon" :class="['mx-auto mb-3 size-8', stat.color]" />
          <p class="text-4xl font-bold text-zinc-900 dark:text-zinc-100">
            {{ stat.value }}
          </p>
          <p class="mt-1 text-sm text-zinc-600 dark:text-zinc-400">
            {{ stat.label }}
          </p>
        </div>
      </div>
    </div>
  </UPageSection>
</template>
