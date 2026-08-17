<script setup lang="ts">
import { nextTick, onMounted, ref, watch } from 'vue'
import L from 'leaflet'
import 'leaflet/dist/leaflet.css'
import { useRoute, useRouter } from 'vue-router'
import FooterApp from '@/components/FooterApp.vue'
import LaporComponent from '@/components/LaporComponent.vue'
import LihatSungaiComponent from '@/components/LihatSungaiComponent.vue'

const route = useRoute()
const router = useRouter()

;(window as unknown as { routingDetail: () => void }).routingDetail = () => {
  router.push('/detail-laporan')
}

const latitude = ref(-7.9666)
const longitude = ref(112.6326)
const isLaporMode = ref(route.query.mode !== 'lihat')
const isLaporVisible = ref(true)

watch(
  () => route.query.mode,
  (newMode) => {
    isLaporMode.value = newMode !== 'lihat'
  },
)

let map: L.Map | null = null
let marker: L.Marker | null = null

watch(isLaporMode, (lapor) => {
  if (lapor) {
    if (map) marker?.addTo(map)
  } else {
    marker?.remove()
  }
})

const onUpdateKoordinat = (coords: { lat: number; lng: number }) => {
  latitude.value = coords.lat
  longitude.value = coords.lng
  marker?.setLatLng([coords.lat, coords.lng])
  map?.setView([coords.lat, coords.lng], 15)
}

const createCustomIcon = (colorClass: string, iconClass: string) => {
  return L.divIcon({
    className: 'custom-map-pin',
    html: `
      <div class="flex flex-col items-center select-none cursor-pointer">
        <div class="w-8 h-8 rounded-full border-2 border-white shadow-md flex items-center justify-center text-white ${colorClass}">
          <i class="${iconClass} text-xs"></i>
        </div>
        <div class="w-2.5 h-2.5 bg-white rotate-45 -mt-1.25 shadow-sm border-r border-b border-black/10"></div>
      </div>
    `,
    iconSize: [32, 40],
    iconAnchor: [16, 40],
    popupAnchor: [0, -40],
  })
}

onMounted(async () => {
  await nextTick()
  map = L.map('map', {
    scrollWheelZoom: false,
    zoomControl: false,
  }).setView([latitude.value, longitude.value], 13)

  L.control
    .zoom({
      position: 'topright',
      zoomInText: '+',
      zoomOutText: '-',
      zoomInTitle: 'Perbesar',
      zoomOutTitle: 'Perkecil',
    })
    .addTo(map)

  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors',
  }).addTo(map)

  const laporIcon = createCustomIcon('bg-[#046C69]', 'pi pi-map-marker')
  marker = L.marker([latitude.value, longitude.value], { draggable: true, icon: laporIcon })
  if (isLaporMode.value) {
    marker.addTo(map)
  }

  marker.on('dragend', (e: L.LeafletEvent) => {
    const pos = (e.target as L.Marker).getLatLng()
    latitude.value = pos.lat
    longitude.value = pos.lng
  })

  const riverData = {
    name: 'Sungai Kalideres',
    location: 'Jakarta Selatan, DKI Jakarta',
    severity: 'Berat',
    reports: 1,
  }

  const staticMarkers = [
    {
      lat: -7.98,
      lng: 112.62,
      name: 'Sungai Brantas Hulu',
      location: 'Klojen, Malang',
      severity: 'Sangat Berat',
      reports: 12,
    },
    {
      lat: -7.95,
      lng: 112.65,
      name: 'Sungai Kalidesa',
      location: 'Lowokwaru, Malang',
      severity: 'Ringan',
      reports: 3,
    },
    {
      lat: -7.965,
      lng: 112.6,
      name: 'Sungai Amprong',
      location: 'Kedungkandang, Malang',
      severity: 'Sedang',
      reports: 5,
    },
  ]

  map.on('click', (e: L.LeafletMouseEvent) => {
    if (!isLaporMode.value) return
    const { lat, lng } = e.latlng
    latitude.value = lat
    longitude.value = lng
    marker?.setLatLng([lat, lng])
  })

  staticMarkers.forEach((item) => {
    let pinColor = 'bg-yellow-500'
    let pinIcon = 'pi pi-exclamation-circle'
    if (item.severity === 'Sangat Berat') {
      pinColor = 'bg-red-500'
      pinIcon = 'pi pi-exclamation-triangle'
    } else if (item.severity === 'Ringan') {
      pinColor = 'bg-emerald-500'
      pinIcon = 'pi pi-info-circle'
    }
    const staticIcon = createCustomIcon(pinColor, pinIcon)

    const staticPopupContent = `
      <div class="w-72 bg-white rounded-2xl overflow-hidden shadow-lg border border-slate-200 flex flex-col font-sans">
        <div class="relative w-full h-32 bg-slate-200">
          <img src="https://images.unsplash.com/photo-1618588507085-c79565432917?w=400&h=200&fit=crop" class="w-full h-full object-cover" alt="Sungai" />
          <span class="absolute top-2 left-2 px-2.5 py-1 bg-black/50 backdrop-blur-md text-white text-[10px] font-semibold rounded-full">
            Belum Diproses
          </span>
        </div>

        <div class="p-4 flex flex-col gap-3">
          <div>
            <h3 class="font-bold text-slate-900 text-base">${item.name}</h3>
            <p class="text-xs text-slate-500 flex items-center gap-1 mt-0.5">
              <i class="pi pi-map-marker"></i> ${item.location}
            </p>
          </div>

          <div class="flex flex-col gap-1.5 border-t border-b border-slate-100 py-2.5 text-xs">
            <div class="flex justify-between items-center">
              <span class="text-slate-500">Tingkat Keparahan</span>
              <span class="font-bold text-red-500">${item.severity}</span>
            </div>
            <div class="flex justify-between items-center">
              <span class="text-slate-500">Jumlah Laporan</span>
              <span class="font-bold text-slate-800 flex items-center gap-1">
                <i class="pi pi-file"></i> ${item.reports}
              </span>
            </div>
          </div>

          <button onclick="routingDetail()" class="w-full py-2.5 bg-[#114B4C] hover:bg-[#0d3b3c] text-white text-xs font-bold rounded-xl flex items-center justify-center gap-2 transition-all cursor-pointer">
            Lihat Detail <i class="pi pi-arrow-right"></i>
          </button>
        </div>
      </div>
    `

    const sMarker = L.marker([item.lat, item.lng], { icon: staticIcon }).addTo(map!)
    sMarker.bindPopup(staticPopupContent, {
      className: 'custom-leaflet-popup',
      maxWidth: 300,
    })
  })

  const popupContent = `
  <div class="w-72 bg-white rounded-2xl overflow-hidden shadow-lg border border-slate-200 flex flex-col font-sans">
    <div class="relative w-full h-32 bg-slate-200">
      <img src="https://images.unsplash.com/photo-1618588507085-c79565432917?w=400&h=200&fit=crop" class="w-full h-full object-cover" alt="Sungai" />
      <span class="absolute top-2 left-2 px-2.5 py-1 bg-black/50 backdrop-blur-md text-white text-[10px] font-semibold rounded-full">
        Belum Diproses
      </span>
    </div>

    <div class="p-4 flex flex-col gap-3">
      <div>
        <h3 class="font-bold text-slate-900 text-base">${riverData.name}</h3>
        <p class="text-xs text-slate-500 flex items-center gap-1 mt-0.5">
          <i class="pi pi-map-marker"></i> ${riverData.location}
        </p>
      </div>


      <div class="flex flex-col gap-1.5 border-t border-b border-slate-100 py-2.5 text-xs">
        <div class="flex justify-between items-center">
          <span class="text-slate-500">Tingkat Keparahan</span>
          <span class="font-bold text-red-500">${riverData.severity}</span>
        </div>
        <div class="flex justify-between items-center">
          <span class="text-slate-500">Jumlah Laporan</span>
          <span class="font-bold text-slate-800 flex items-center gap-1">
            <i class="pi pi-file"></i> ${riverData.reports}
          </span>
        </div>
      </div>


      <button onclick="routingDetail()" class="w-full py-2.5 bg-[#114B4C] hover:bg-[#0d3b3c] text-white text-xs font-bold rounded-xl flex items-center justify-center gap-2 transition-all cursor-pointer">
        Lihat Detail <i class="pi pi-arrow-right"></i>
      </button>
    </div>
  </div>
  `

  marker.bindPopup(popupContent, {
    className: 'custom-leaflet-popup',
    maxWidth: 300,
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
            class="w-fit h-10 bg-[#046C69] rounded-full flex flex-row justify-center gap-2 items-center px-2 py-7 shadow-lg mb-5 z-40"
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
        <div id="map" class="w-full h-180 shadow-lg z-10"></div>
        <LaporComponent
          :isLaporMode="isLaporMode"
          :isLaporVisible="isLaporVisible"
          :koordinat="`${latitude}, ${longitude}`"
          @toggleLaporVisible="isLaporVisible = !isLaporVisible"
          @update-koordinat="onUpdateKoordinat"
        />
        <LihatSungaiComponent :isLaporMode="isLaporMode" />
        <div
          class="absolute bottom-28 flex flex-col gap-2 right-12 z-500 bg-white shadow-2xl px-4 py-3 rounded-lg text-xs"
        >
          <p class="font-bold text-xs text-black">Tingkat Keparahan</p>
          <div class="grid grid-cols-2 gap-2 justify-start items-start w-full">
            <div class="flex flex-row justify-start items-center gap-2">
              <div class="w-2 h-2 bg-red-500 rounded-full"></div>
              <p class="text-black font-regular text-xs text-left">Sangat Berat</p>
            </div>
            <div class="flex flex-row justify-start items-center gap-2">
              <div class="w-2 h-2 bg-green-500 rounded-full"></div>
              <p class="text-black font-regular text-xs text-left">Ringan</p>
            </div>
            <div class="flex flex-row justify-start items-center gap-2">
              <div class="w-2 h-2 bg-yellow-500 rounded-full"></div>
              <p class="text-black font-regular text-xs text-left">Sedang</p>
            </div>
          </div>
        </div>
      </div>
    </section>
    <div class="w-full bg-[#083C42]">
      <FooterApp />
    </div>
  </div>
</template>
