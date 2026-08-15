<script setup lang="ts">
const props = defineProps({
  title: String,
  description: String,
  icon: String,
})
</script>

<template>
  <div
    class="flex flex-row justify-center items-start w-full border-black/10 gap-6 border-2 rounded-xl p-8 shadow-lg hover:"
  >
    <i
      :class="`pi pi-${props.icon} bg-[#006672] rounded-full p-2 text-white`"
      style="font-size: 2rem"
    ></i>
    <div class="flex flex-col">
      <h4 class="text-lg font-bold">{{ props.title }}</h4>
      <p class="text-md text-[#3E494B] font-regular">
        {{ props.description }}
      </p>
    </div>
  </div>
</template>
