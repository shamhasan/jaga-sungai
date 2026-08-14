<script setup lang="ts">
const handleEventClick = () => {
  console.log('Event clicked')
}
</script>
<template>
  <div
    class="w-full bg-[#083C42] h-28 rounded-xl grid grid-cols-[1fr_6fr] shadow-lg gap-4 p-5 cursor-pointer hover:scale-102 transition-transform duration-300"
    @click="handleEventClick"
  >
    <div class="bg-white rounded-xl flex flex-col items-center justify-center text-[#083C42]">
      <h1 class="text-xl font-bold">24</h1>
      <p class="text-sm font-regular">Juli</p>
    </div>
    <div class="rounded-xl flex flex-col items-start justify-center text-white">
      <p class="text-sm text-white/70 flex items-center justify-center gap-2">
        <i class="pi pi-clock"></i> 08.00 - 12.00 WIB
      </p>
      <h2 class="text-lg font-semibold">Membersihkan Sungai Kalideres</h2>
      <p class="text-sm text-white/70 flex items-center justify-center gap-2">
        <i class="pi pi-map-marker"></i>Sungai Kalideres, Jakarta Barat
      </p>
    </div>
  </div>
</template>
