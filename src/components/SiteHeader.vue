<script setup>
import { ref, onMounted } from 'vue'

/* =========================================================
   TEMA TERANG / GELAP
   ========================================================= */
const THEME_KEY = 'portfolio-theme'
const isDarkMode = ref(false)

const applyTheme = (dark) => {
  isDarkMode.value = dark
  document.body.classList.toggle('dark', dark)
}

const toggleTheme = () => {
  applyTheme(!isDarkMode.value)
  localStorage.setItem(THEME_KEY, isDarkMode.value ? 'dark' : 'light')
}

onMounted(() => {
  const saved = localStorage.getItem(THEME_KEY)
  const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches
  applyTheme(saved ? saved === 'dark' : prefersDark)
})
</script>

<template>
  <header class="navbar">
    <div class="nav-container">
      <a class="brand-name" href="#home">adndrsd</a>

      <nav class="nav-menu" aria-label="Navigasi utama">
        <a href="#home">HOME</a>
        <a href="#about-me">ABOUT</a>
        <a href="#projects">PROJECTS</a>
        <a href="#experiences">EXPERIENCES</a>
        <a href="#contact-me">CONTACT</a>
      </nav>

      <button
        class="theme-btn"
        type="button"
        :aria-label="isDarkMode ? 'Beralih ke mode terang' : 'Beralih ke mode gelap'"
        @click="toggleTheme"
      >
        <svg v-if="isDarkMode" class="theme-icon" viewBox="0 0 24 24" aria-hidden="true">
          <circle cx="12" cy="12" r="4" />
          <path d="M12 2v2M12 20v2M4.93 4.93l1.41 1.41M17.66 17.66l1.41 1.41M2 12h2M20 12h2M4.93 19.07l1.41-1.41M17.66 6.34l1.41-1.41" />
        </svg>
        <svg v-else class="theme-icon" viewBox="0 0 24 24" aria-hidden="true">
          <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z" />
        </svg>
      </button>
    </div>
  </header>
</template>