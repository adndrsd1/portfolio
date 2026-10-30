<script setup>
import { nextTick, onMounted } from 'vue'
import SiteHeader from './components/SiteHeader.vue'
import MainPage from './components/MainPage.vue'

onMounted(() => {
  const id = decodeURIComponent(window.location.hash.slice(1))
  if (!id) return
  nextTick(() => document.getElementById(id)?.scrollIntoView())
})
</script>

<template>
  <SiteHeader />
  <main>
    <MainPage />
  </main>
</template>