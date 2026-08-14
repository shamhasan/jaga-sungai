<template>
  <div
    class="w-141 bg-[#ffffff] h-141 rounded-2xl shadow-xl cursor-pointer hover:scale-101 transition-transform duration-400"
  >
    <div class="flex flex-row items-start justify-center h-5/8">
      <div
        class="w-1/2 h-full rounded-tl-2xl bg-[url('../assets/images/sungai-before.png')] bg-cover bg-center p-4 flex items-start"
      >
        <div class="bg-black/50 rounded-full px-4 py-0.5 w-fit mr-auto">
          <p class="text-white uppercase font-regular text-xs">BEFORE</p>
        </div>
      </div>
      <div class="w-0.5 h-full bg-[#43E6D0] blur-xs"></div>

      <div
        class="w-1/2 h-full rounded-tr-2xl bg-[url('../assets/images/sungai-after.png')] bg-cover bg-center p-4 flex items-start"
      >
        <div class="bg-[#11B981] rounded-full px-4 py-0.5 w-fit ml-auto">
          <p class="text-white uppercase font-regular text-xs">AFTER</p>
        </div>
      </div>
    </div>
    <div class="flex flex-col items-start justify-start p-8 h-3/8">
      <div class="flex flex-row items-center justify-between gap-2 w-full">
        <h4 class="text-black font-bold text-2xl">Sungai Ciliwung</h4>
        <div class="bg-[#11B981] rounded-md px-4 py-0.5 w-fit">
          <p class="text-white uppercase font-regular text-xs">Selesai</p>
        </div>
      </div>
      <div class="bg-black/10 rounded-md my-2 px-2 py-0.5 w-fit">
        <p class="text-black uppercase font-regular text-xs">COORD: 6.2588° S, 106.7629° E</p>
      </div>
      <hr class="w-full border-t border-black/50 my-4" />
      <div class="flex flex-row items-center justify-between gap-2 w-full">
        <div class="flex flex-col items-start">
          <p class="text-black font-regular text-xs uppercase">Duration</p>
          <p class="text-black/60 font-regular text-md">14 Months</p>
        </div>
        <div class="flex flex-col items-start">
          <p class="text-black font-regular text-xs uppercase">Volunters</p>
          <p class="text-black/60 font-regular text-md">450+</p>
        </div>
        <div class="flex flex-col items-start">
          <p class="text-black font-regular text-xs uppercase">Last Inspection</p>
          <p class="text-black/60 font-regular text-md">24 Juli 2026</p>
        </div>
      </div>
    </div>
  </div>
</template>
