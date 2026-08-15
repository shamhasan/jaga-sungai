<script setup lang="ts">
import { nextTick, onMounted, ref } from 'vue'
import L from 'leaflet'
import 'leaflet/dist/leaflet.css'

const latitude = ref(-7.9666)
const longitude = ref(112.6326)

let map: L.Map | null = null
let marker: L.Marker | null = null

onMounted(async () => {
  await nextTick()
  map = L.map('map').setView([latitude.value, longitude.value], 13)

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
          class="absolute top-[210px] w-full left-0 right-0 h-45 blur-xl bg-gradient-to-b from-[#175252] to-[#86D4D4] z-20 pointer-events-none scale-x-110"
        ></div> -->
        <div class="relative flex flex-col w-full text-white justify-center items-center z-30">
          <h1 class="text-white text-[60px] font-bold mt-20">Peta Sungai Tercemar</h1>
          <p>Pantau semua sungai tercemar di Indonesia</p>
        </div>
      </div>
    </section>
    <section>
      <div class="relative flex flex-col gap-4 w-full mt-20 z-10">
        <div id="map" class="w-full h-[700px] shadow-lg"></div>
      </div>
    </section>
  </div>
</template>
