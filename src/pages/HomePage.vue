<script setup lang="ts">
import { ref } from 'vue'
import StepCard from '../components/StepCard.vue'
import EventList from '../components/EventList.vue'
import FooterApp from '../components/FooterApp.vue'
import ReportCard from '../components/ReportCard.vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const routingPetaSungai = () => {
  router.push({ path: '/peta-sungai', query: { mode: 'lihat' } })
}

const routingLapor = () => {
  router.push({ path: '/peta-sungai', query: { mode: 'lapor' } })
}

const isLaporHovered = ref(false)
</script>

<template>
  <div class="w-full">
    <div class="absolute inset-0 -z-20 w-full h-full">
      <img
        src="../assets/images/Beranda.webp"
        alt="Background"
        class="w-full h-full object-cover object-top blur-1"
      />
    </div>
    <section
      class="relative min-h-screen w-full flex flex-col items-center justify-center overflow-hidden"
    >
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
            @click="routingLapor"
            class="px-8 py-3 bg-[#4FC4C4] hover:bg-white text-white hover:text-[#4FC4C4] font-semibold rounded-xl shadow-md transition-transform duration-300 active:scale-95 cursor-pointer"
          >
            LAPORKAN SUNGAI
          </button>

          <button
            class="px-8 py-3 bg-white/20 hover:bg-white text-white hover:text-[#4FC4C4] font-semibold rounded-xl shadow-md border border-white/20 backdrop-blur-md transition-transform duration-300 active:scale-95 cursor-pointer"
            @click="routingPetaSungai"
          >
            LIHAT PETA
          </button>
        </div>
      </div>
    </section>

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
              <img src="../assets/icons/lapor-icon.png" style="width: 40px" alt="" />
            </template>
          </StepCard>
          <StepCard
            title="Verifikasi"
            description="Komunitas dan relawan lokal memverifikasi kondisi lapangan."
          >
            <template #icon>
              <img src="../assets/icons/verifikasi-icon.png" style="width: 40px" alt="" />
            </template>
          </StepCard>
          <StepCard
            title="Bersihkan"
            description="Aksi gotong royong pembersihan sungai diorganisir bersama dinas terkait."
          >
            <template #icon>
              <img src="../assets/icons/bersihkan-icon.png" style="width: 35px" alt="" />
            </template>
          </StepCard>
          <StepCard
            title="Update"
            description="Pantau perkembangan sungai dan bagikan cerita keberhasilan komunitas."
          >
            <template #icon>
              <img src="../assets/icons/update-icon.png" style="width: 35px" alt="" />
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
            <EventList />
            <EventList />
            <EventList />
            <button
              class="w-full bg-white h-14 rounded-full mt-4 cursor-pointer hover:translate-y-1 transition-all duration-200 text-[#256E6E] font-semibold uppercase"
              @click="routingPetaSungai"
            >
              Lihat peta sungai
            </button>
          </div>
          <div class="flex flex-col gap-2">
            <div class="w-full bg-[#083C42] h-115 rounded-2xl">
              <iframe
                class="w-full h-full rounded-2xl"
                src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d64132.509919540884!2d106.66769966323635!3d-6.136144975706978!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e6a02a65782c999%3A0xe29088fa56313d07!2sKec.%20Kalideres%2C%20Kota%20Jakarta%20Barat%2C%20Daerah%20Khusus%20Ibukota%20Jakarta!5e1!3m2!1sid!2sid!4v1786715647516!5m2!1sid!2sid"
                width="600"
                height="450"
                style="border: 0"
                allowfullscreen="false"
                loading="lazy"
                referrerpolicy="strict-origin-when-cross-origin"
              ></iframe>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section>
      <div class="min-h-screen w-full text-white p-24 px-48">
        <h2 class="text-[49px] md:text-5xl font-bold tracking-wider drop-shadow-md text-white">
          Laporan Sungai Bersih
        </h2>
        <div class="grid grid-cols-1 gap-4 w-full mt-6 items-center">
          <div class="flex flex-row gap-2">
            <p class="text-[16.57px] font-regular text-white drop-shadow-sm w-full">
              Laporan sungai-sungai yang sudah bersih dan <br />
              sudah dapat penganganan lebih lanjut
            </p>
            <div class="h-18 rounded-2xl flex flex-row items-center justify-center gap-4">
              <i
                class="pi pi-arrow-left bg-[#083C42] text-white p-3 rounded-full cursor-pointer"
                style="font-size: 1.5rem"
              ></i>
              <i
                class="pi pi-arrow-right bg-[#083C42] text-white p-3 rounded-full cursor-pointer"
                style="font-size: 1.5rem"
              ></i>
            </div>
          </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-8 w-full mt-6">
          <div class="flex flex-col gap-2">
            <ReportCard />
          </div>
          <div class="flex flex-col gap-2">
            <ReportCard />
          </div>
        </div>
      </div>
    </section>
    <section>
      <div class="w-full min-h-168 px-48 flex flex-col items-center justify-center">
        <h1
          class="text-[71.5px] md:text-5xl font-semibold tracking-wider drop-shadow-md text-white mb-4"
        >
          JOIN THE MOVEMENT
        </h1>
        <p class="text-lg font-regular text-white drop-shadow-sm w-1/2 text-center mb-4">
          Bersama kita bisa mengembalikan kejernihan sungai-sungai Indonesia. Dapatkan update aksi
          dan laporan terkini.
        </p>
        <div class="flex flex-row-[3fr_1fr] justify-between items-center gap-4 w-1/2 mt-6">
          <input
            type="email"
            placeholder="Alamat Email Anda"
            class="w-full bg-black/25 border-2 border-white h-full py-4 rounded-2xl px-4 text-white"
          />
          <button
            class="min-w-fit h-full bg-white py-4 px-6 rounded-2xl cursor-pointer transition-all duration-200 text-sm text-[#256E6E] font-semibold uppercase"
            @click="{}"
          >
            Gabung Sekarang
          </button>
        </div>
      </div>
    </section>
    <FooterApp />
  </div>
</template>
