<script setup lang="ts">
import { ref } from 'vue'
import Button from 'primevue/button'
import logo from '../assets/images/logo-jagasungai.png'

interface NavItem {
  label: string
  path: string
}

const navMenus = ref<NavItem[]>([
  { label: 'Beranda', path: '/' },
  { label: 'Peta Sungai', path: '/peta-sungai' },
  { label: 'Tentang Kami', path: '/about' },
  { label: 'Kontak', path: '/contact' },
])

const isScrolled = ref(false)

window.addEventListener('scroll', () => {
  isScrolled.value = window.scrollY > 0
})
</script>

<template>
  <header
    :class="{
      'bg-linear-to-b from-[#083C42]/80 to-[#083C42]/0 h-20': isScrolled,
    }"
    class="w-full h-20 bg-transparent sticky px-10 top-0 z-50"
  >
    <div class="w-full h-full max-w-8xl mx-auto flex items-center justify-between">
      <router-link to="/" class="flex items-center gap-2.5 no-underline">
        <img :src="logo" alt="Logo" class="h-7 object-cover" />
      </router-link>

      <nav
        class="flex items-center gap-2 p-1.5 rounded-full bg-[#105A5C]/10 backdrop-blur-lg border border-white/20 shadow-white/50 shadow-xs"
      >
        <router-link
          v-for="menu in navMenus"
          :key="menu.path"
          :to="menu.path"
          class="px-8 py-1 rounded-full text-[14px] font-regular text-white/50 hover:text-white hover:text-[16px] transition-all no-underline"
          active-class="!text-white font-bold shadow-xs text-[16px]"
        >
          {{ menu.label }}
        </router-link>
      </nav>

      <div class="flex items-center gap-3">
        <Button
          label="Lapor Sungai"
          class="bg-white! hover:bg-white/90! text-[#175F63]! border-none! px-4.5! py-2! rounded-full! text-[14px]! font-medium! shadow-sm! transition-all! ease-in-out! duration-300! hover:scale-110!"
        />
      </div>
    </div>
  </header>
</template>
