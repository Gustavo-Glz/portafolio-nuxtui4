<template>
  <section class="mt-28 flex flex-col items-center justify-center gap-8">
    <span
      class="bg-primary flex size-32 items-center justify-center rounded-full text-4xl font-bold text-white"
    >
      GM
    </span>
    <h1 class="text-4xl font-bold lg:text-5xl">
      Hola, soy <span class="text-primary">Gustavo González</span>
    </h1>
    <h2 class="text-2xl font-semibold text-slate-500 lg:text-3xl dark:text-slate-400">
      Desarrollador Full Stack
    </h2>
    <p class="w-2/3 text-center text-lg text-slate-500 dark:text-slate-400">
      Creo soluciones digitales innovadoras y escalables usando tecnologías modernas. Especializado
      en React, Node.js y arquitectura en la nube con +5 años de experiencia.
    </p>
    <div class="flex gap-10">
      <UButton
        to="mailto:gustavo.gonzalez.montalvo@gmail.com"
        class="cursor-pointer px-4"
        size="lg"
        color="primary"
        icon="ic:outline-email"
      >
        Contactar
      </UButton>
      <UButton
        to="https://drive.google.com/file/d/1p8EJnRWgdqyWSI5zuIkAETNGgFEVRh15/view?usp=sharing"
        class="cursor-pointer px-4"
        size="lg"
        color="neutral"
        icon="material-symbols:download-rounded"
        download
      >
        Descargar CV
      </UButton>
    </div>
    <div class="mt-10 flex gap-10">
      <UButton
        to="https://github.com/Gustavo-Glz"
        icon="line-md:github"
        size="xl"
        color="neutral"
        variant="ghost"
        target="_blank"
        aria-label="GitHub"
      ></UButton>
      <UButton
        to="https://www.linkedin.com/in/gustavo-gonz%C3%A1lez-montalvo-7aa92a228/"
        icon="line-md:linkedin"
        size="xl"
        color="neutral"
        variant="ghost"
        target="_blank"
        aria-label="LinkedIn"
      ></UButton>
      <UButton
        to="mailto:gustavo.gonzalez.montalvo@gmail.com"
        icon="ic:outline-email"
        size="xl"
        color="neutral"
        variant="ghost"
        target="_blank"
        aria-label="Email"
      ></UButton>
    </div>
    <UIcon class="mt-10 size-7 animate-bounce" name="line-md:arrow-down" />
  </section>
</template>
