<script setup lang="ts">
const props = defineProps({
  judul: String,
  isi: String,
  deskripsi: String,
})
</script>

<template>
  <div class="flex flex-col gap-3 w-full h-full">
    <div
      class="flex flex-row gap-2 justify-between items-start w-full h-full bg-[url(../assets/images/bg-stats-lihat-sungai.png)] bg-cover-w rounded-2xl py-4 px-8 bg-center bg-no-repeat shadow-2xl!"
    >
      <div class="w-1/2 h-ful rounded-xl flex flex-col">
        <p class="text-white text-sm font-semibold">{{ props.judul }}</p>
        <p class="text-white text-4xl font-bold">{{ props.isi }}</p>
        <p class="text-white text-sm font-regular">{{ props.deskripsi }}</p>
      </div>
      <div class="w-8 h-8 flex items-center justify-center bg-white rounded-full">
        <i class="pi pi-map-marker text-2xl font- text-[#046C69]"></i>
      </div>
    </div>
  </div>
</template>
