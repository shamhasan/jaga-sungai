<script setup lang="ts">
import AppBar from './components/AppBar.vue'
</script>

<template>
  <div class="relative w-full min-h-screen">
    <header class="fixed top-0 left-0 w-full z-50 h-18 bg-transparent">
      <AppBar />
    </header>

    <main>
      <router-view />
    </main>
  </div>
</template>
