<script setup lang="ts">
import { ref } from 'vue'
import StepCard from '../components/StepCard.vue'

const isLaporHovered = ref(false)
</script>

<template>
  <div class="w-full">
    <div class="absolute inset-0 -z-20 w-full h-full">
      <img
        src="../assets/images/Beranda.webp"
        alt="Background"
        class="w-full h-full object-cover object-top"
      />
    </div>
    <section
      class="relative min-h-screen w-full flex flex-col items-center justify-center overflow-hidden"
    >
      <!-- Garbage/Hero Asset Overlay -->
      <div
        class="absolute inset-0 -z-10 w-full h-full pointer-events-none overflow-hidden flex items-center justify-center mt-24"
      >
        <img
          src="../assets/images/asset-hero.webp"
          alt="Asset Sampah"
          class="w-full max-w-8xl h-full max-h-screen object-contain object-center transition-all duration-1000"
          :class="{
            'ease-in-out scale-125 translate-y-30 rotate-2 opacity-0': isLaporHovered,
          }"
        />
      </div>

      <!-- Hero Content -->
      <div
        class="relative z-10 text-center text-white max-w-4xl px-6 py-12 flex flex-col items-center gap-6"
      >
        <h1
          class="text-4xl md:text-6xl text-white font-bold tracking-wider leading-tight drop-shadow-md transition-transform duration-1000 origin-center"
          :class="{ 'scale-105': isLaporHovered }"
        >
          JAGA SUNGAI, <br />
          JAGA KEHIDUPAN
        </h1>

        <p
          class="text-white text-lg font-medium max-w-2xl drop-shadow-sm transition-transform duration-1000 origin-center"
          :class="{ 'scale-105': isLaporHovered }"
        >
          Platform kolaborasi komunitas untuk memantau, melaporkan, dan memulihkan ekosistem sungai
          Indonesia.
        </p>

        <div class="flex flex-col sm:flex-row gap-4 mt-2 transition-all duration-1000">
          <button
            @mouseenter="isLaporHovered = true"
            @mouseleave="isLaporHovered = false"
            class="px-8 py-3 bg-[#4FC4C4] hover:bg-white text-white hover:text-[#4FC4C4] font-semibold rounded-xl shadow-md transition-transform duration-300 active:scale-95 cursor-pointer"
          >
            LAPORKAN SUNGAI
          </button>

          <button
            class="px-8 py-3 bg-white/20 hover:bg-white text-white hover:text-[#4FC4C4] font-semibold rounded-xl shadow-md border border-white/20 backdrop-blur-md transition-transform duration-300 active:scale-95 cursor-pointer"
          >
            LIHAT PETA
          </button>
        </div>
      </div>
    </section>

    <!-- Section 2: How It Works Section (Scroll Lanjutan) -->
    <section
      class="min-h-screen w-full text-white flex flex-col items-center justify-center py-24 px-6"
    >
      <div class="max-w-7xl mx-auto flex flex-col items-center text-center gap-12">
        <h2 class="text-[40px] md:text-5xl font-bold tracking-wider drop-shadow-md">
          How its work?
        </h2>

        <div class="grid grid-cols-1 md:grid-cols-4 gap-8 w-full mt-6">
          <StepCard
            title="Lapor"
            description="Temukan sungai tercemar dan kirimkan laporan beserta foto dan lokasi."
          >
            <template #icon>
              <img src="../assets/icons/lapor-icon.png" alt="" />
            </template>
          </StepCard>
          <StepCard
            title="Verifikasi"
            description="Komunitas dan relawan lokal memverifikasi kondisi lapangan."
          >
            <template #icon>
              <img src="../assets/icons/verifikasi-icon.png" alt="" />
            </template>
          </StepCard>
          <StepCard
            title="Bersihkan"
            description="Aksi gotong royong pembersihan sungai diorganisir bersama dinas terkait."
          >
            <template #icon>
              <img src="../assets/icons/bersihkan-icon.png" alt="" />
            </template>
          </StepCard>
          <StepCard
            title="Update"
            description="Pantau perkembangan sungai dan bagikan cerita keberhasilan komunitas."
          >
            <template #icon>
              <img src="../assets/icons/update-icon.png" alt="" />
            </template>
          </StepCard>
        </div>
      </div>
    </section>

    <section>
      <div class="min-h-screen w-full text-white p-24 px-48">
        <h2 class="text-[50px] md:text-5xl font-bold tracking-wider drop-shadow-md text-white">
          Mari Ikut Membersihkan Sungai
        </h2>
        <div class="grid grid-cols-1 md:grid-cols-[5fr_2fr] gap-8 w-full mt-6 items-center">
          <div class="flex flex-col gap-2">
            <p class="text-lg font-regular text-white drop-shadow-sm">
              Pantau semua kegiatan membersihkan sungai terdekat!
            </p>
          </div>

          <div class="flex flex-col gap-6">
            <div
              class="w-full bg-[#083C42] h-10 rounded-full shadow-md flex items-center justify-between px-4 gap-3"
            >
              <div class="flex items-center gap-2 min-w-0">
                <i class="pi pi-map-marker text-white/70" style="font-size: 1.5rem"></i>
                <p
                  class="text-white/70 font-medium uppercase text-xs sm:text-sm overflow-hidden text-ellipsis whitespace-nowrap px-3"
                >
                  Detecting location...
                </p>
              </div>
              <button
                class="hover:text-white text-[#4FC4C4] font-semibold uppercase text-xs sm:text-sm transition-colors cursor-pointer shrink-0"
              >
                CHANGE
              </button>
            </div>
          </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-8 w-full mt-6">
          <div class="flex flex-col gap-4 grid-rows-4">
            <div class="w-full bg-amber-300 h-28 rounded-2xl"></div>
            <div class="w-full bg-amber-300 h-28 rounded-2xl"></div>
            <div class="w-full bg-amber-300 h-28 rounded-2xl"></div>
            <div class="w-full bg-amber-300 h-14 rounded-full mt-10"></div>
          </div>
          <div class="flex flex-col gap-2">
            <div class="w-full bg-amber-300 h-115 rounded-2xl"></div>
          </div>
        </div>
      </div>
    </section>
    <div class="min-h-screen w-full text-white p-24 px-48">
      <h2 class="text-[50px] md:text-5xl font-bold tracking-wider drop-shadow-md text-white">
        Laporan Sungai Bersih
      </h2>
      <div class="grid grid-cols-1 md:grid-cols-[5fr_2fr] gap-4 w-full mt-6 items-center">
        <div class="flex flex-col gap-2">
          <p class="text-lg font-regular text-white drop-shadow-sm">
            Laporan sungai-sungai yang sudah bersih dan sudah dapat penganganan lebih lanjut
          </p>
        </div>
      </div>
    </div>

    <section></section>
  </div>
</template>
