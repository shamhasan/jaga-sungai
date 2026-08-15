<script setup lang="ts">
defineProps<{
  title: string
  description: string
}>()
</script>

<template>
  <div class="relative pt-16 max-w-sm w-full">
    <div class="absolute top-3 left-1/2 -translate-x-1/2 z-10">
      <div
        class="w-24 h-24 rounded-full bg-[#2F8E8E] p-1 flex items-center justify-center shadow-md"
      >
        <div
          class="w-full h-full bg-white rounded-full flex items-center justify-center p-4 [&_img]:w-12 [&_img]:h-12 [&_img]:object-contain"
        >
          <slot name="icon"> </slot>
        </div>
      </div>
    </div>

    <div
      class="w-65 h-65 bg-white rounded-3xl px-6 pb-6 pt-16 text-center shadow-2xl border-4 border-[#2F8E8E] text-[#256E6E] relative card-notch hover:bg-[#2F8E8E] hover:text-white duration-300 transition-all flex flex-col justify-center items-center gap-2"
    >
      <h3 class="text-xl font-bold leading-snug">
        {{ title }}
      </h3>
      <p class="text-sm leading-relaxed">
        {{ description }}
      </p>
    </div>
  </div>
</template>

<style scoped>
.card-notch {
  -webkit-mask-image: radial-gradient(circle 54px at 50% -1.5px, transparent 100%, black 100%);
  mask-image: radial-gradient(circle 54px at 50% -1.5px, transparent 100%, black 100%);
}
</style>
