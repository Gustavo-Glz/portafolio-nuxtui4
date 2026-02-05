<template>
  <section class="mt-28 flex flex-col items-center justify-center gap-8">
    <span
      class="bg-primary text-highlighted flex size-32 items-center justify-center rounded-full text-4xl font-bold"
    >
      GM
    </span>
    <h1 class="text-highlighted text-4xl font-bold md:text-5xl lg:text-6xl">
      Hola, soy <span class="text-primary">Gustavo González</span>
    </h1>
    <h2 class="text-muted text-2xl md:text-3xl">Desarrollador Full Stack</h2>
    <p class="text-muted text-center md:w-2/3 md:text-lg">
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
        class="text-muted"
        to="https://github.com/Gustavo-Glz"
        icon="line-md:github"
        size="xl"
        color="neutral"
        variant="ghost"
        target="_blank"
        aria-label="GitHub"
      ></UButton>
      <UButton
        class="text-muted"
        to="https://www.linkedin.com/in/gustavo-gonz%C3%A1lez-montalvo-7aa92a228/"
        icon="line-md:linkedin"
        size="xl"
        color="neutral"
        variant="ghost"
        target="_blank"
        aria-label="LinkedIn"
      ></UButton>
      <UButton
        class="text-muted"
        to="mailto:gustavo.gonzalez.montalvo@gmail.com"
        icon="ic:outline-email"
        size="xl"
        color="neutral"
        variant="ghost"
        target="_blank"
        aria-label="Email"
      ></UButton>
    </div>
    <UIcon class="text-muted mt-10 size-7 animate-bounce" name="line-md:arrow-down" />
  </section>
</template>
