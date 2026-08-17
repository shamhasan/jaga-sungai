<script setup lang="ts">
import InputText from 'primevue/inputtext'
import StatsList from './StatsList.vue'

const props = defineProps<{
  isLaporMode: boolean
}>()
</script>

<template>
  <Transition
    enter-active-class="transition duration-300 ease-out"
    enter-from-class="transform opacity-0 -translate-x-10"
    enter-to-class="transform opacity-100 translate-x-0"
    leave-active-class="transition duration-200 ease-in"
    leave-from-class="transform opacity-100 translate-x-0"
    leave-to-class="transform opacity-0 -translate-x-10"
  >
    <div
      v-if="!props.isLaporMode"
      class="absolute top-36 left-12 right-12 z-200 p-4 flex items-center justify-center w-1/4 flex-col gap-4 transition-all! duration-300! ease-in-out!"
    >
      <div class="flex flex-row justify-between items-center w-full gap-2">
        <div class="relative w-full">
          <i
            class="absolute left-3 top-1/2 -translate-y-1/2 text-black/40 hover:text-black/60 flex items-center pi pi-search"
            style="font-size: 1rem"
          ></i>
          <InputText
            label="Lokasi"
            placeholder="Cari daerah atau sungai"
            class="w-full pl-9! pr-10! py-2! rounded-xl! border-[#01606C]/70! bg-white! text-sm! font-regular! text-black! focus:text-black! border! outline-none! focus:border-[#01606C]! focus:outline-none!"
          />
        </div>
        <div
          class="relative w-fit bg-white rounded-xl border border-[#075158] flex flex-row items-center gap-2 px-4 py-2"
        >
          <p class="text-[#334155] font-regular text-sm text-left">Filter</p>
          <i class="pi pi-filter text-sm text-[#334155]"></i>
        </div>
      </div>
      <StatsList judul="Total Lokasi" isi="132" deskripsi="Titik sungai tercemar" />
      <StatsList judul="Belum Proses" isi="56" deskripsi="Lokasi" />
      <StatsList judul="Dalam Proses" isi="20" deskripsi="Lokasi" />
      <StatsList judul="Selesai Dibersihkan" isi="56" deskripsi="Lokasi" />
    </div>
  </Transition>
</template>
