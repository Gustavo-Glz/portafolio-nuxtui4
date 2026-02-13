<script setup lang="ts">
const contactMethods = ref([
  {
    title: 'Email',
    description: 'gustavo.gonzalez.montalvo@gmail.com',
    icon: 'i-heroicons-envelope',
    link: 'mailto:gustavo.gonzalez.montalvo@gmail.com',
    color: 'from-blue-500 to-blue-600',
    bgColor: 'bg-blue-500'
  },
  {
    title: 'GitHub',
    description: 'github.com/Gustavo-Glz',
    icon: 'i-simple-icons-github',
    link: 'https://github.com/Gustavo-Glz',
    target: '_blank',
    color: 'from-zinc-700 to-zinc-900',
    bgColor: 'bg-zinc-800'
  },
  {
    title: 'LinkedIn',
    description: 'gustavo-gonzalez-montalvo',
    icon: 'i-simple-icons-linkedin',
    link: 'https://www.linkedin.com/in/gustavo-gonz%C3%A1lez-montalvo-7aa92a228/',
    target: '_blank',
    color: 'from-blue-600 to-blue-700',
    bgColor: 'bg-blue-600'
  }
])

const isLoaded = ref(false)

onMounted(() => {
  setTimeout(() => {
    isLoaded.value = true
  }, 100)

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
    id="contact"
    description="¿Tienes un proyecto en mente? Hablemos sobre cómo puedo ayudarte"
  >
    <template #title>
      <h2 class="text-4xl font-light">
        Trabajemos
        <span class="font-semibold text-blue-600 dark:text-blue-400">Juntos</span>
      </h2>
    </template>

    <div>
      <div
        class="scroll-reveal relative overflow-hidden rounded-3xl bg-linear-to-br from-zinc-100 to-zinc-50 p-8 md:p-12 dark:from-zinc-900 dark:to-zinc-800"
      >
        <div
          class="absolute -top-20 -right-20 h-64 w-64 rounded-full bg-blue-500/10 blur-3xl"
        ></div>
        <div
          class="absolute -bottom-20 -left-20 h-64 w-64 rounded-full bg-blue-500/10 blur-3xl"
        ></div>

        <div class="relative z-10">
          <p class="mb-8 text-center text-lg text-zinc-600 dark:text-zinc-400">
            Estoy disponible para proyectos freelance, oportunidades laborales o simplemente para
            <span class="font-medium text-zinc-800 dark:text-zinc-200"
              >conectar y conocer nuevas tecnologías</span
            >.
          </p>

          <UPageGrid>
            <a
              v-for="method in contactMethods"
              :key="method.title"
              :href="method.link"
              :target="method.target"
              class="card-hover group flex flex-col items-center rounded-2xl bg-white p-6 text-center shadow-lg shadow-zinc-200/50 dark:bg-zinc-700/50 dark:shadow-zinc-800/50"
            >
              <div
                class="mb-4 flex h-14 w-14 items-center justify-center rounded-xl transition-transform duration-300 group-hover:scale-110"
                :class="method.bgColor"
              >
                <UIcon :name="method.icon" class="size-7 text-white" />
              </div>
              <h3 class="mb-1 font-semibold text-zinc-800 dark:text-zinc-200">
                {{ method.title }}
              </h3>
              <p class="text-sm text-zinc-600 dark:text-zinc-400">
                {{ method.description }}
              </p>
            </a>
          </UPageGrid>

          <div class="mt-10 flex flex-col items-center gap-4 sm:flex-row sm:justify-center">
            <UButton
              to="mailto:gustavo.gonzalez.montalvo@gmail.com"
              size="lg"
              color="primary"
              icon="i-heroicons-envelope"
              class="cursor-pointer shadow-lg shadow-blue-500/25 hover:shadow-blue-500/40"
            >
              Enviar Email
            </UButton>
            <UButton
              to="https://drive.google.com/file/d/1p8EJnRWgdqyWSI5zuIkAETNGgFEVRh15/view?usp=sharing"
              size="lg"
              variant="outline"
              color="neutral"
              icon="i-heroicons-arrow-down-tray"
              download
              class="cursor-pointer"
            >
              Descargar CV
            </UButton>
          </div>
        </div>
      </div>

      <div class="scroll-reveal mt-12 text-center">
        <p class="text-sm text-zinc-500 dark:text-zinc-500">
          © {{ new Date().getFullYear() }} Gustavo González. Construido con
          <span class="font-medium text-zinc-700 dark:text-zinc-300">Nuxt + Nuxt UI</span>
        </p>
      </div>
    </div>
  </UPageSection>
</template>
