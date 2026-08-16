<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps({
  title: String,
  description: String,
  icon: String,
})

const isHovered = ref(false)
</script>

<template>
  <div
    @mouseenter="isHovered = true"
    @mouseleave="isHovered = false"
    class="flex flex-row justify-center items-start w-full border-black/10 gap-6 border-2 rounded-xl p-8 shadow-2xl transition-all duration-300 cursor-default"
    :class="{ 'bg-[#006672]': isHovered }"
  >
    <i
      :class="[
        `pi pi-${props.icon} rounded-full p-2 transition-colors duration-300`,
        isHovered ? 'bg-white text-[#006672]' : 'bg-[#006672] text-white',
      ]"
      style="font-size: 2rem"
    ></i>
    <div class="flex flex-col transition-colors duration-300" :class="{ 'text-white': isHovered }">
      <h4 class="text-lg font-bold">{{ props.title }}</h4>
      <p
        class="text-md font-regular transition-colors duration-300"
        :class="isHovered ? 'text-white/80' : 'text-[#3E494B]'"
      >
        {{ props.description }}
      </p>
    </div>
  </div>
</template>
