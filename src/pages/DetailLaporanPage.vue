<script setup lang="ts">
import FooterApp from '@/components/FooterApp.vue'
import { Button } from 'primevue'
import { useRouter } from 'vue-router'

const router = useRouter()

const openGoogleMaps = () => {
  window.open('https://maps.app.goo.gl/69v9K1ABj45yuhwG6', '_blank')
}
</script>
<template>
  <section>
    <div class="w-full h-full flex flex-col items-start justify-start px-42 py-8 mb-10">
      <div class="absolute inset-0 -z-20 w-full h-full">
        <img
          src="../assets/images/Beranda.webp"
          alt="Background"
          class="w-full h-full object-cover object-top blur-1"
        />
      </div>
      <div
        class="absolute inset-0 -z-10 w-full h-full bg-linear-to-t from-black/50 to-black/10"
      ></div>
      <Button
        label="Kembali ke Peta"
        icon="pi pi-arrow-left"
        class="mt-25 bg-[#084F4F]! text-white! border-none! shadow-md"
        @click="router.push('/peta-sungai')"
      />
      <div
        class="w-fit h-full flex justify-center items-center px-2 py-1 mt-10 bg-[#FEFFC3] rounded-full"
      >
        <p class="text-[#EAB308] text-xs font-bold">Sedang berlangsung</p>
      </div>
      <div class="relative flex flex-col w-full text-white justify-start items-start mb-10">
        <h1 class="text-white text-[60px] font-bold">Detail Laporan</h1>
        <div class="flex flex-row justify-start items-center gap-2">
          <i class="pi pi-map-marker text-white/80" style="font-size: 1.5rem"></i>
          <p class="text-white/80 text-md font-regular">Jakarta Selatan, DKI Jakarta</p>
        </div>
        <p class="text-white/80 text-md font-regular mt-2 w-2/3">
          Saya sebagai warga setempat ingin melaporkan penumpukan sampah limbah rumah tangga di
          aliran Sungai Kalimalang yang kini sangat menumpuk hingga airnya berwarna cokelat gelap
          serta menimbulkan bau tidak sedap. Kondisi ini sangat mengkhawatirkan karena berpotensi
          memicu banjir saat musim hujan tiba serta membahayakan kesehatan anak-anak sekolah yang
          sering lewat di area ini.
        </p>
      </div>
    </div>
  </section>
  <section>
    <div class="w- h-full bg-white flex flex-row justify-start items-start px-42 py-12 gap-4">
      <div class="flex flex-col justify-start items-start gap-4 w-2/3">
        <div
          class="flex flex-col w-full justify-start items-start border border-black/20 rounded-xl h-full p-4"
        >
          <p class="text-black text-md font-bold">Lokasi</p>
          <div class="rounded-lg w-full h-50 overflow-hidden relative">
            <iframe
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d5734.450849730808!2d106.70127546111722!3d-6.136022131753875!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e6a02a65782c999%3A0xe29088fa56313d07!2sKec.%20Kalideres%2C%20Kota%20Jakarta%20Barat%2C%20Daerah%20Khusus%20Ibukota%20Jakarta!5e0!3m2!1sid!2sid!4v1786958821702!5m2!1sid!2sid"
              width="500"
              height="260"
              style="border: 0"
              scrolling="no"
              loading="lazy"
              class="absolute -top-14 left-0 pointer-events-none"
              referrerpolicy="strict-origin-when-cross-origin"
            ></iframe>
          </div>
          <div class="flex flex-row gap-2 mt-4">
            <i class="pi pi-map-marker text-black/80" style="font-size: 1rem"></i>
            <p class="text-black/80 text-sm font-semibold">
              Jakarta Selatan, DKI Jakarta <br /><span class="text-xs font-regular text-black/60"
                >6°08'11.5"S 106°42'01.9"E
              </span>
            </p>
          </div>
          <Button
            label="Lihat di Google Maps"
            icon="pi pi-external-link"
            iconPos="right"
            class="mt-4 bg-gray-50! text-[#008B9C]! border! border-[#008B9C]! w-full shadow-md"
            @click="openGoogleMaps"
          />
        </div>

        <div
          class="flex flex-col w-full justify-start items-start border border-black/20 rounded-xl h-full p-4 gap-2"
        >
          <p class="text-black text-md font-bold">Informasi Sungai</p>
          <div class="flex flex-row w-full justify-between items-center py-2">
            <p class="text-[13px] font-semibold flex justify-center items-center text-black/50">
              <i class="pi pi-arrows-h mr-3"></i>Panjang
            </p>
            <p class="text-black text-[13px] font-semibold">120 Km</p>
          </div>
          <div class="border-b border-black/10 w-full"></div>

          <div class="flex flex-row w-full justify-between items-center py-2">
            <p class="text-[13px] font-semibold flex justify-center items-center text-black/50">
              <i class="pi pi-arrow-up-right-and-arrow-down-left-from-center mr-3"></i>Lebar
              Rata-rata
            </p>
            <p class="text-black text-[13px] font-semibold">20 - 50 m</p>
          </div>
          <div class="border-b border-black/10 w-full"></div>

          <div class="flex flex-row w-full justify-between items-center py-2">
            <p class="text-[13px] font-semibold flex justify-center items-center text-black/50">
              <img src="../assets/icons/ic-daerah-aliran.png" class="mr-3 w-4 h-4" alt="" />Daerah
              Aliran
            </p>
            <p class="text-black text-[13px] font-semibold">Bogor - Jakarta</p>
          </div>
          <div class="border-b border-black/10 w-full"></div>

          <div class="flex flex-row w-full justify-between items-center py-2">
            <p class="text-[13px] font-semibold flex justify-center items-center text-black/50">
              <img src="../assets/icons/ic-jenis-sungai.png" class="mr-3 w-4 h-4" alt="" />Jenis
              Sungai
            </p>
            <p class="text-black text-[13px] font-semibold">Sungai Utama</p>
          </div>
          <div class="border-b border-black/10 w-full"></div>

          <div class="flex flex-row w-full justify-between items-center py-2">
            <p class="text-[13px] font-semibold flex justify-center items-center text-black/50">
              <i class="pi pi-info-circle mr-3"></i>Status
            </p>
            <p class="text-[#EAB308] bg-[#FEFFC3] px-2 py-1 rounded-md text-[13px] font-semibold">
              Sedang Berlangsung
            </p>
          </div>
          <div class="border-b border-black/10 w-full"></div>
        </div>

        <div
          class="flex flex-col w-full h-full bg-[#F2F9FA] rounded-xl p-8 border border-[#CFEAEC]"
        >
          <p class="text-black text-[21px] font-bold">Ingin membantu membersihkan sungai?</p>
          <p class="text-[#6B7280] text-[15.65px] font-regular py-2">
            Bergabunglah dengan komunitas relawan di sekitar lokasi ini untuk aksi bersih sungai.
          </p>
          <Button
            label="Gabung Sekarang"
            class="mt-4 bg-[#008B9C]! text-white! border! border-[#008B9C]! w-fit shadow-md"
          />
        </div>
      </div>

      <div class="flex flex-col w-full justify-start items-start gap-4">
        <div
          class="flex flex-col w-full justify-start items-start border border-black/20 rounded-xl h-full p-4 gap-2"
        >
          <p class="text-black text-md font-bold">Foto Laporan</p>
          <div
            class="w-full h-50 rounded-xl bg-[url(../assets/images/image-laporan.png)] bg-cover bg-center overflow-hidden"
          ></div>
        </div>
        <div
          class="flex flex-col w-full justify-start items-start border border-black/20 rounded-xl h-full p-4 gap-2"
        >
          <p class="text-black text-md font-bold">Deskripsi Laporan</p>
          <p class="text-black text-sm font-regular text-justify">
            Saya sebagai warga setempat ingin melaporkan penumpukan sampah limbah rumah tangga di
            aliran Sungai Kalimalang yang kini sangat menumpuk hingga airnya berwarna cokelat gelap
            serta menimbulkan bau tidak sedap. Kondisi ini sangat mengkhawatirkan karena berpotensi
            memicu banjir saat musim hujan tiba serta membahayakan kesehatan anak-anak sekolah yang
            sering lewat di area ini.
          </p>
        </div>

        <div class="flex flex-row w-full h-full gap-4">
          <div class="flex flex-col w-full h-full border border-black/20 rounded-xl p-4 gap-2">
            <p class="text-black text-md font-bold">Timeline Laporan</p>
            <div class="w-full h-full flex flex-col justify-start items-start mt-8">
              <div class="flex gap-4 relative">
                <div class="absolute left-5 top-10 bottom-[-24px] w-0.5 bg-black/20"></div>
                <div
                  class="relative z-10 w-10 h-10 rounded-full bg-[#BAEADA] flex items-center justify-center shrink-0"
                >
                  <div class="w-6 h-6 flex items-center justify-center bg-[#10B981] rounded-full">
                    <i class="pi pi-check text-[#BAEADA] text-[10px] font-bold"></i>
                  </div>
                </div>

                <div class="flex flex-col pb-6">
                  <span class="text-xs text-slate-400">5 Agustus 2025, 14:32</span>
                  <h4 class="font-bold text-black text-sm">Laporan Diterima</h4>
                  <p class="text-xs text-slate-500">
                    Laporan berhasil dikirim dan menunggu verifikasi.
                  </p>
                </div>
              </div>

              <div class="flex gap-4 relative mt-4">
                <div class="absolute left-5 top-10 bottom-[-24px] w-0.5 bg-black/20"></div>

                <div
                  class="relative z-10 w-10 h-10 rounded-full bg-emerald-100 flex items-center justify-center shrink-0"
                >
                  <div class="w-6 h-6 flex items-center justify-center bg-[#10B981] rounded-full">
                    <i class="pi pi-check text-[#BAEADA] text-[10px] font-bold"></i>
                  </div>
                </div>

                <div class="flex flex-col pb-6">
                  <h4 class="font-bold text-black text-sm">Verifikasi</h4>
                  <p class="text-xs text-slate-500">
                    Laporan akan diverifikasi oleh tim JagaSungai.
                  </p>
                </div>
              </div>

              <div class="flex gap-4 relative mt-4">
                <div class="absolute left-5 top-10 bottom-[-24px] w-0.5 bg-slate-200"></div>

                <div
                  class="relative z-10 w-10 h-10 rounded-full bg-emerald-100 flex items-center justify-center shrink-0"
                >
                  <div class="w-6 h-6 flex items-center justify-center bg-[#10B981] rounded-full">
                    <i class="pi pi-check text-[#BAEADA] text-[10px] font-bold"></i>
                  </div>
                </div>

                <div class="flex flex-col pb-6">
                  <h4 class="font-bold text-black text-sm">Tindak Lanjut</h4>
                  <p class="text-xs text-slate-500">
                    Jika laporan valid, akan diteruskan ke pihak terkait.
                  </p>
                </div>
              </div>

              <div class="flex gap-4 relative mt-4">
                <div
                  class="relative z-10 w-10 h-10 rounded-full bg-slate-100 flex items-center justify-center shrink-0"
                >
                  <div class="w-6 h-6 flex items-center justify-center bg-slate-400 rounded-full">
                    <i class="pi pi-check text-[#BAEADA] text-[10px] font-bold"></i>
                  </div>
                </div>

                <div class="flex flex-col">
                  <h4 class="font-bold text-slate-400 text-sm">Selesai</h4>
                  <p class="text-xs text-slate-400">Masalah telah ditangani dan diperbarui.</p>
                </div>
              </div>
            </div>
          </div>
          <div class="flex flex-col w-130 h-full border border-black/20 rounded-xl p-4 gap-2">
            <p class="text-black/80 text-xs font-bold uppercase">Status Saat Ini</p>
            <div class="flex flex-row w-full h-full justify-center items-center gap-2">
              <div
                class="w-10 h-10 flex items-center justify-center bg-[#FEFCE8] rounded-full border border-[#FEF08A] shrink-0"
              >
                <img src="../assets/icons/ic-onprogress.png" alt="" width="12" height="12" />
              </div>
              <div class="flex flex-col">
                <p class="text-black text-sm font-bold">Sedang Berlangsung</p>
                <p class="text-black/80 text-xs font-regular">
                  Laporan ini sudah diverifikasi oleh tim JagaSungai.
                </p>
              </div>
            </div>
            <div class="w-full h-full border border-[#E5E7EB] border-0.5 rounded-xl"></div>
            <div class="flex flex-col gap-2 mt-2">
              <div class="flex items-center justify-between">
                <div class="flex items-center gap-2 text-slate-500">
                  <i class="pi pi-calendar text-sm"></i>
                  <span class="text-xs font-medium">Dilaporkan pada</span>
                </div>
                <span class="text-xs font-bold text-slate-800">5 Agustus 2025, 14:32</span>
              </div>

              <div class="flex items-center justify-between">
                <div class="flex items-center gap-2 text-slate-500">
                  <i class="pi pi-user text-sm"></i>
                  <span class="text-xs font-medium">Dilaporkan oleh</span>
                </div>
                <div class="flex items-center gap-2">
                  <img
                    src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=100&h=100&fit=crop&crop=faces"
                    alt="Avatar"
                    class="w-5 h-5 rounded-full object-cover"
                  />
                  <span class="text-xs font-bold text-slate-800">Rina Setyowati</span>
                </div>
              </div>

              <div class="flex items-center justify-between">
                <div class="flex items-center gap-2 text-slate-500">
                  <i class="pi pi-tag text-sm"></i>
                  <span class="text-xs font-medium">ID Laporan</span>
                </div>
                <span class="text-xs font-bold text-slate-800">#JS-250805-0012</span>
              </div>
            </div>
            <div
              class="flex flex-col gap-2 mt-2 bg-[#FEFCE8] border border-[#FEF08A] rounded-lg p-4"
            >
              <p class="text-black text-xs font-semibold">Jadwal Pembersihan sudah ditentukan</p>
              <div class="flex items-center justify-between py-2 border-b border-slate-100">
                <span class="text-xs font-regular text-slate-500">Tanggal</span>
                <span class="text-xs font-regular text-amber-800">12 Agustus 2025</span>
              </div>

              <!-- Baris 2: Waktu -->
              <div class="flex items-center justify-between py-2 border-b border-slate-100">
                <span class="text-xs font-regular text-slate-500">Waktu</span>
                <span class="text-xs font-regular text-amber-800">08:00 - 12:00 WIB</span>
              </div>

              <!-- Baris 3: Koordinator -->
              <div class="flex items-center justify-between py-2">
                <span class="text-xs font-regular text-slate-500">Koordinator</span>
                <span class="text-xs font-regular text-amber-800">Tim Kebersihan DKI</span>
              </div>

              <!-- Bagian Pengingat (Footer Note) -->
              <div class="pt-2">
                <p class="text-xs text-slate-600 leading-relaxed">
                  <strong class="text-slate-700 font-regular italic">Pengingat:</strong>
                  <span class="italic text-slate-500"
                    >Jadwal dapat berubah sewaktu-waktu tergantung kondisi cuaca.</span
                  >
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
  <FooterApp />
</template>
