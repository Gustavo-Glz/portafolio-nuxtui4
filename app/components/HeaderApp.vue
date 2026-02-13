<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const activeSection = ref('')
const isAutoScrolling = ref(false)

const updateURLHash = (sectionId: string) => {
  if (!isAutoScrolling.value) {
    history.replaceState(history.state, '', `#${sectionId}`)
  }
}

const scrollToSection = (sectionId: string) => {
  activeSection.value = ''
  isAutoScrolling.value = true

  nextTick(() => {
    const element = document.getElementById(sectionId)
    if (element) {
      const headerHeight = 60
      const elementPosition = element.getBoundingClientRect().top + window.pageYOffset
      const offsetPosition = elementPosition - headerHeight

      window.scrollTo({
        top: offsetPosition,
        behavior: 'smooth'
      })

      if (sectionId === 'about') {
        setTimeout(() => {
          activeSection.value = 'about'
          updateURLHash('about')
        }, 800)
      }
    } else {
      window.scrollTo({
        top: document.body.scrollHeight,
        behavior: 'smooth'
      })
    }

    setTimeout(() => {
      isAutoScrolling.value = false
    }, 1500)
  })
}

const scrollToTop = () => {
  activeSection.value = ''
  isAutoScrolling.value = true

  nextTick(() => {
    history.replaceState(history.state, '', window.location.pathname)

    window.scrollTo({
      top: 0,
      behavior: 'smooth'
    })

    setTimeout(() => {
      isAutoScrolling.value = false
    }, 1500)
  })
}

const checkIfAtTop = () => {
  if (!isAutoScrolling.value && window.scrollY < 50) {
    activeSection.value = ''
    history.replaceState(history.state, '', window.location.pathname)
  }
}

onMounted(() => {
  window.addEventListener('scroll', checkIfAtTop, { passive: true })

  const observerOptions = {
    root: null,
    rootMargin: '-15% 0px -55% 0px',
    threshold: 0.1
  }

  const observer = new IntersectionObserver((entries) => {
    if (!isAutoScrolling.value && window.scrollY >= 50) {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          if (entry.intersectionRatio > 0.1) {
            activeSection.value = entry.target.id
            updateURLHash(entry.target.id)
          }
        }
      })
    }
  }, observerOptions)

  const sections = ['about', 'skills', 'projects', 'experience', 'education', 'contact']
  sections.forEach((sectionId) => {
    const element = document.getElementById(sectionId)
    if (element) {
      observer.observe(element)
    }
  })

  onUnmounted(() => {
    window.removeEventListener('scroll', checkIfAtTop)
    sections.forEach((sectionId) => {
      const element = document.getElementById(sectionId)
      if (element) {
        observer.unobserve(element)
      }
    })
  })
})

const items = computed<NavigationMenuItem[]>(() => [
  {
    label: 'Sobre Mí',
    to: '#about',
    active: activeSection.value === 'about',
    click: () => scrollToSection('about')
  },
  {
    label: 'Skills',
    to: '#skills',
    active: activeSection.value === 'skills',
    click: () => scrollToSection('skills')
  },
  {
    label: 'Proyectos',
    to: '#projects',
    active: activeSection.value === 'projects',
    click: () => scrollToSection('projects')
  },
  {
    label: 'Experiencia',
    to: '#experience',
    active: activeSection.value === 'experience',
    click: () => scrollToSection('experience')
  },
  {
    label: 'Educación',
    to: '#education',
    active: activeSection.value === 'education',
    click: () => scrollToSection('education')
  },
  {
    label: 'Contacto',
    to: '#contact',
    active: activeSection.value === 'contact',
    click: () => scrollToSection('contact')
  }
])
</script>

<template>
  <UHeader>
    <template #title>
      <button class="cursor-pointer" @click="scrollToTop">
        <span class="font-heading text-xl font-bold text-zinc-900 dark:text-zinc-100">GM</span>
      </button>
    </template>

    <UNavigationMenu :items="items" />

    <template #right>
      <UColorModeButton class="cursor-pointer" />
      <UButton to="#contact" class="cursor-pointer">Contactar</UButton>
    </template>

    <template #body>
      <UNavigationMenu :items="items" orientation="vertical" class="-mx-2.5" />
    </template>
  </UHeader>
</template>
