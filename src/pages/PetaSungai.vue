<script setup lang="ts">
import { nextTick, onMounted, ref } from 'vue'
import L from 'leaflet'
import 'leaflet/dist/leaflet.css'
import FooterApp from '@/components/FooterApp.vue'
import LaporComponent from '@/components/LaporComponent.vue'
import InputText from 'primevue/inputtext'

const latitude = ref(-7.9666)
const longitude = ref(112.6326)
const isLaporMode = ref(true)
const isLaporVisible = ref(true)

let map: L.Map | null = null
let marker: L.Marker | null = null

onMounted(async () => {
  await nextTick()
  map = L.map('map', {
    scrollWheelZoom: false,
    zoomControl: false,
  }).setView([latitude.value, longitude.value], 13)

  L.control
    .zoom({
      position: 'bottomright',
    })
    .addTo(map)

  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors',
  }).addTo(map)

  marker = L.marker([latitude.value, longitude.value], { draggable: true }).addTo(map)

  marker.on('dragend', (e: any) => {
    const pos = e.target.getLatLng()
    latitude.value = pos.lat
    longitude.value = pos.lng
  })

  // 5. Update koordinat saat peta diklik
  map.on('click', (e: any) => {
    const { lat, lng } = e.latlng
    latitude.value = lat
    longitude.value = lng
    marker?.setLatLng([lat, lng])
  })

  map.invalidateSize()
})
</script>

<template>
  <div class="w-full">
    <section>
      <div class="w-full h-full flex flex-col items-start justify-center p-8">
        <div class="absolute inset-0 -z-20 w-full h-3/8">
          <img
            src="../assets/images/Beranda.webp"
            alt="Background"
            class="w-full h-full object-cover object-top blur-1"
          />
        </div>
        <!-- <div
          class="absolute top-[270px] w-full left-0 right-0 h-45 blur-md bg-gradient-to-b from-[#175252] via-[#86D4D4] to-[#86D4D4]/70 z-20 pointer-events-none scale-x-110"
        ></div> -->
        <div class="relative flex flex-col w-full text-white justify-center items-center z-30">
          <h1 class="text-white text-[60px] font-bold mt-25">Peta Sungai Tercemar</h1>
          <p>Pantau semua sungai tercemar di Indonesia</p>
        </div>
      </div>
    </section>

    <section>
      <div class="relative flex flex-col gap-4 w-full">
        <div class="flex flex-col gap-2 justify-center items-center">
          <div
            class="w-fit h-10 bg-[#046C69] rounded-full flex flex-row justify-center gap-2 items-center px-2 py-7 shadow-lg mb-10 z-40"
          >
            <p
              class="text-white uppercase font-semibold text-md rounded-full px-4 py-2 cursor-pointer transition-all! duration-300! ease-in-out!"
              @click="isLaporMode = true"
              :class="{
                'bg-white text-[#046C69]!': isLaporMode,
              }"
            >
              Laporkan Sungai
            </p>
            <p
              class="text-white uppercase font-semibold text-md rounded-full px-4 py-2 cursor-pointer transition-all! duration-300! ease-in-out!"
              @click="isLaporMode = false"
              :class="{
                'bg-white text-[#046C69]!': !isLaporMode,
              }"
            >
              Lihat sungai
            </p>
          </div>
        </div>
        <div id="map" class="w-full h-190 shadow-lg z-10"></div>
        <LaporComponent
          :isLaporMode="isLaporMode"
          :isLaporVisible="isLaporVisible"
          @toggleLaporVisible="isLaporVisible = !isLaporVisible"
        />
        <div
          v-if="!isLaporMode"
          class="absolute top-36 left-12 right-12 z-[500] p-4 flex items-center justify-center w-1/4 flex-col gap-4 transition-all! duration-300! ease-in-out!"
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
                class="w-full pl-9! pr-10! py-2! rounded-xl! border-[#075158]! bg-white! text-sm! font-regular! text-black/60! focus:text-black! border! outline-none! focus:border-black/70! focus:outline-none!"
              />
            </div>
            <div
              class="relative w-fit bg-white rounded-xl border border-[#075158] flex flex-row items-center gap-2 px-4 py-3"
            >
              <p class="text-black uppercase font-semibold text-xs text-left">Filter</p>
              <i class="pi pi-filter text-2xl text-black/60"></i>
            </div>
          </div>
        </div>
        <!-- <div
          class="absolute bottom-4 left-4 z-500 bg-slate-900/70 backdrop-blur-sm text-white px-3 py-2 rounded-lg text-xs"
        >
          Lat: -7.9666, Lng: 112.6326
        </div> -->
      </div>
    </section>
    <div class="w-full bg-[#083C42]">
      <FooterApp />
    </div>
  </div>
</template>
