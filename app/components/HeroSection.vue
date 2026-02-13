<script setup lang="ts">
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
  <section class="relative overflow-hidden py-32 lg:py-40">
    <div class="absolute inset-0 -z-10">
      <div
        class="absolute inset-0 bg-[radial-gradient(ellipse_at_top,_var(--tw-gradient-stops))] from-blue-50/80 via-transparent to-transparent dark:from-blue-950/30"
      ></div>
      <div
        class="absolute top-0 right-0 h-[500px] w-[500px] translate-x-1/3 -translate-y-1/4 rounded-full bg-blue-200/40 blur-3xl dark:bg-blue-800/20"
      ></div>
      <div
        class="absolute bottom-0 left-0 h-[400px] w-[400px] -translate-x-1/3 translate-y-1/4 rounded-full bg-zinc-200/40 blur-3xl dark:bg-zinc-800/30"
      ></div>
      <div class="absolute inset-0 bg-[url('/grid.svg')] opacity-[0.03] dark:opacity-[0.02]"></div>
    </div>

    <div
      class="container mx-auto flex flex-col items-center justify-center gap-8 px-4"
      :class="{ 'opacity-0': !isLoaded }"
    >
      <div
        class="relative mb-4"
        :class="{ 'translate-y-8 opacity-0': !isLoaded, 'translate-y-0 opacity-100': isLoaded }"
        style="transition: all 0.8s cubic-bezier(0.16, 1, 0.3, 1)"
      >
        <div class="relative">
          <div
            class="absolute -inset-6 rounded-full bg-gradient-to-r from-blue-400 to-blue-600 opacity-30 blur-3xl"
          ></div>
          <div
            class="bg-primary relative flex size-28 items-center justify-center rounded-full text-3xl font-bold ring-4 ring-blue-500/20 md:size-32 md:text-4xl"
            style="animation: float 6s ease-in-out infinite"
          >
            GM
          </div>
        </div>
        <div
          class="absolute -top-2 -right-2 flex h-8 w-8 items-center justify-center rounded-full bg-blue-500 text-white ring-4 ring-blue-500/30"
          :class="{ 'scale-0': !isLoaded, 'scale-100': isLoaded }"
          style="transition: all 0.5s cubic-bezier(0.34, 1.56, 0.64, 1) 0.4s"
        >
          <UIcon name="i-heroicons-hand-raised" class="size-4" />
        </div>
      </div>

      <div class="text-center">
        <p
          class="mb-3 text-sm font-medium tracking-widest text-blue-600 uppercase dark:text-blue-400"
          :class="{ 'translate-y-8 opacity-0': !isLoaded, 'translate-y-0 opacity-100': isLoaded }"
          style="transition: all 0.6s cubic-bezier(0.16, 1, 0.3, 1)"
        >
          Portafolio Personal
        </p>
        <h1
          class="mb-4 text-5xl font-light tracking-tight text-zinc-900 md:text-6xl lg:text-7xl dark:text-zinc-100"
          :class="{ 'translate-y-8 opacity-0': !isLoaded, 'translate-y-0 opacity-100': isLoaded }"
          style="transition: all 0.8s cubic-bezier(0.16, 1, 0.3, 1) 0.1s"
        >
          Hola, soy
          <span class="font-semibold text-blue-600 dark:text-blue-400">Gustavo González</span>
        </h1>

        <div
          class="overflow-hidden"
          :class="{ 'max-h-0 opacity-0': !isLoaded, 'max-h-24 opacity-100': isLoaded }"
          style="transition: all 0.6s cubic-bezier(0.16, 1, 0.3, 1) 0.2s"
        >
          <h2 class="text-xl font-light text-zinc-600 md:text-2xl dark:text-zinc-400">
            Desarrollador Full Stack
          </h2>
        </div>
      </div>

      <p
        class="max-w-2xl text-center text-lg leading-relaxed text-zinc-600 md:text-xl dark:text-zinc-400"
        :class="{ 'translate-y-8 opacity-0': !isLoaded, 'translate-y-0 opacity-100': isLoaded }"
        style="transition: all 0.8s cubic-bezier(0.16, 1, 0.3, 1) 0.3s"
      >
        Creo soluciones digitales innovadoras y escalables usando tecnologías modernas.
        <span class="font-medium text-zinc-800 dark:text-zinc-200"
          >Especializado en React, Node.js y arquitectura en la nube</span
        >
        con +5 años de experiencia.
      </p>

      <div
        class="flex flex-wrap justify-center gap-4"
        :class="{ 'translate-y-8 opacity-0': !isLoaded, 'translate-y-0 opacity-100': isLoaded }"
        style="transition: all 0.8s cubic-bezier(0.16, 1, 0.3, 1) 0.4s"
      >
        <UButton
          to="mailto:gustavo.gonzalez.montalvo@gmail.com"
          size="lg"
          color="primary"
          icon="i-heroicons-envelope"
          class="cursor-pointer shadow-lg shadow-blue-500/25 hover:shadow-blue-500/40"
        >
          Contactar
        </UButton>
        <UButton
          to="https://drive.google.com/file/d/1p8EJnRWgdqyWSI5zuIkAETNGgFEVRh15/view?usp=sharing"
          size="lg"
          color="neutral"
          variant="outline"
          icon="i-heroicons-arrow-down-tray"
          download
          class="cursor-pointer"
        >
          Descargar CV
        </UButton>
      </div>

      <div
        class="flex gap-3"
        :class="{ 'translate-y-8 opacity-0': !isLoaded, 'translate-y-0 opacity-100': isLoaded }"
        style="transition: all 0.8s cubic-bezier(0.16, 1, 0.3, 1) 0.5s"
      >
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

      <div
        class="scroll-reveal mt-16"
        :class="{ 'opacity-0': !isLoaded, 'opacity-100': isLoaded }"
        style="transition: opacity 0.8s 0.7s"
      >
        <div class="flex flex-col items-center gap-3 text-zinc-400">
          <span class="text-xs font-medium tracking-widest uppercase">Explorar</span>
          <div class="relative">
            <div class="absolute -inset-4 animate-pulse rounded-full bg-blue-500/10"></div>
            <div
              class="relative flex h-12 w-7 items-start justify-center rounded-full border-2 border-zinc-300 p-1 dark:border-zinc-600"
            >
              <div class="h-2 w-1 animate-bounce rounded-full bg-zinc-400"></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
