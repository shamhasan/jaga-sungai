<script setup lang="ts">
import { nextTick, onMounted, ref } from 'vue'
import L from 'leaflet'
import 'leaflet/dist/leaflet.css'
import FooterApp from '@/components/FooterApp.vue'
import InputText from 'primevue/inputtext'
import RadioButton from 'primevue/radiobutton'

const latitude = ref(-7.9666)
const longitude = ref(112.6326)
const selectedValue = ref()

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
          class="absolute top-[210px] w-full left-0 right-0 h-45 blur-xl bg-gradient-to-b from-[#175252] to-[#86D4D4] z-20 pointer-events-none scale-x-110"
        ></div> -->
        <div class="relative flex flex-col w-full text-white justify-center items-center z-30">
          <h1 class="text-white text-[60px] font-bold mt-25">Peta Sungai Tercemar</h1>
          <p>Pantau semua sungai tercemar di Indonesia</p>
        </div>
      </div>
    </section>
    <section>
      <div class="relative flex flex-col gap-4 w-full mt-20 z-10">
        <div class="flex flex-col gap-2 justify-center items-center">
          <div
            class="w-fit h-10 bg-[#046C69] rounded-full flex flex-row justify-center gap-2 items-center px-2 py-7 shadow-lg"
          >
            <p
              class="text-[#046C69] uppercase font-semibold text-md bg-white rounded-full px-4 py-2 cursor-pointer"
            >
              Laporkan Sungai
            </p>
            <p
              class="text-[#046C69] uppercase font-semibold text-md bg-white rounded-full px-4 py-2 cursor-pointer"
            >
              Lihat sungai
            </p>
          </div>
        </div>
        <div id="map" class="w-full h-170 shadow-lg"></div>
        <div
          class="absolute top-36 left-12 right-12 z-[400] p-4 flex items-center justify-center w-1/4 flex-col gap-4"
        >
          <div
            class="bg-[url(../assets/images/bg-button-lapor.png)] bg-fit bg-top bg-no-repeat rounded-md px-4 py-4 cursor-pointer w-full flex items-center justify-center"
          >
            <h4 class="font-bold text-white text-md uppercase">Laporkan Pencemaran sungai</h4>
          </div>

          <div
            class="flex flex-col justify-center items-start w-full h-full p-6 bg-white rounded-md gap-2"
          >
            <p class="text-black uppercase font-semibold text-xs text-left">Lokasi</p>
            <div class="relative w-full">
              <InputText
                placeholder="Masukkan lokasi anda"
                class="w-full pl-3! pr-10! py-2! rounded-md! border-black/20! bg-black/10! text-sm! font-regular! text-black/60! focus:text-black! border! outline-none! focus:border-black/70! focus:outline-none!"
                required
              />
              <button
                class="absolute right-1 top-1 bottom-1 px-3 active:scale-95 text-black rounded-md flex items-center justify-center transition-all cursor-pointer"
              >
                <i class="pi pi-map-marker" style="font-size: 1rem"></i>
              </button>
            </div>
            <p class="text-black uppercase font-semibold text-xs text-left">Tingkat keparahan</p>
            <div class="relative w-full">
              <div
                class="bg-[url(../assets/images/level-indikator.png)] bg-no-repeat w-full h-2 rounded-md"
                style="background-size: cover; background-position: center"
              ></div>
              <div class="flex flex-row justify-between items-center w-full py-2">
                <RadioButton
                  v-model="selectedValue"
                  value="1"
                  :pt="{
                    box: { class: 'border-2 border-red-500! bg-red-100! hover:border-red-600!' },
                    icon: { class: 'bg-red-800!' },
                  }"
                />
                <RadioButton
                  v-model="selectedValue"
                  value="2"
                  :pt="{
                    box: { class: 'border-2 border-red-500! bg-red-100! hover:border-red-600!' },
                    icon: { class: 'bg-red-800!' },
                  }"
                />
                <RadioButton
                  v-model="selectedValue"
                  value="3"
                  :pt="{
                    box: { class: 'border-2 border-red-500! bg-red-100! hover:border-red-600!' },
                    icon: { class: 'bg-red-800!' },
                  }"
                />
                <RadioButton
                  v-model="selectedValue"
                  value="4"
                  :pt="{
                    box: { class: 'border-2 border-red-500! bg-red-100! hover:border-red-600!' },
                    icon: { class: 'bg-red-800!' },
                  }"
                />
                <RadioButton
                  v-model="selectedValue"
                  value="5"
                  :pt="{
                    box: { class: 'border-2 border-red-500! bg-red-100! hover:border-red-600!' },
                    icon: { class: 'bg-red-800!' },
                  }"
                />
              </div>
              <div class="flex flex-row gap-2"></div>
              <!-- <RadioButton  -->
            </div>
          </div>
        </div>

        <!-- Komponen Lain di Pojok Bawah (Contoh: Legend / Status GPS) -->
        <div
          class="absolute bottom-4 left-4 z-[400] bg-slate-900/70 backdrop-blur-sm text-white px-3 py-2 rounded-lg text-xs"
        >
          Lat: -7.9666, Lng: 112.6326
        </div>
      </div>
    </section>
    <div class="w-full bg-[#083C42]">
      <FooterApp />
    </div>
  </div>
</template>
