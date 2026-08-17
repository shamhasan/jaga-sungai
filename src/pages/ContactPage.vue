<script setup lang="ts">
import FooterApp from '@/components/FooterApp.vue'
</script>

<template>
  <section>
    <div class="w-full min-h-screen flex flex-col items-start justify-center px-42 py-8">
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
      <div class="relative flex flex-col w-full text-white justify-center items-center mt-25 mb-10">
        <h1 class="text-white text-[60px] font-bold">Kontak JagaSungai</h1>
        <p>Bersama Memulihkan Nadi Kehidupan</p>
      </div>
      <div class="flex flex-row w-full h-full mb-30">
        <div
          class="flex flex-col w-200 h-125 p-8 bg-[url(../assets/images/bg-left-panel-contact.png)] rounded-l-xl bg-fit bg-center"
        >
          <h1 class="text-[32px] font-bold text-white">Mari Terhubung</h1>
          <p class="text-[14px] font-regular text-white">
            Punya pertanyaan atau ingin berkolaborasi? Tim kami siap membantu Anda mewujudkan sungai
            yang lebih bersih.
          </p>
          <div class="flex flex-row justify-start gap-3 items-start mt-10">
            <i class="pi pi-map-marker pt-1.5 text-[#6FD5E7]" style="font-size: 1.5rem"></i>
            <div class="flex flex-col justify-start items-start">
              <p class="text-[18px] font-bold text-white pb-1">Kantor Pusat</p>
              <p class="text-[14px] font-sm text-white/80">
                Jalan Cempaka Wangi No. 22 <br />
                Jakarta Selatan
              </p>
            </div>
          </div>
          <div class="flex flex-row justify-start gap-3 items-start mt-4">
            <i class="pi pi-envelope pt-1.5 text-[#6FD5E7]" style="font-size: 1.5rem"></i>
            <div class="flex flex-col justify-start items-start">
              <p class="text-[18px] font-bold text-white pb-1">Email</p>
              <p class="text-[14px] font-sm text-white/80">halo@jagasungai.id</p>
            </div>
          </div>
          <div class="flex flex-row justify-start gap-3 items-start mt-4">
            <i class="pi pi-phone pt-1.5 text-[#6FD5E7]" style="font-size: 1.5rem"></i>
            <div class="flex flex-col justify-start items-start">
              <p class="text-[18px] font-bold text-white pb-1">Telepon</p>
              <p class="text-[14px] font-sm text-white/80">+62 812-3456-7890</p>
            </div>
          </div>

          <div class="flex flex-row justify-start items-center gap-4 mt-8">
            <div class="w-10 h-10 bg-[#197580] rounded-full flex justify-center items-center">
              <img src="../assets/icons/icon-fb.png" style="width: 18px" alt="" />
            </div>
            <div class="w-10 h-10 bg-[#197580] rounded-full flex justify-center items-center">
              <i class="pi pi-twitter" style="font-size: 1rem"></i>
            </div>
            <div class="w-10 h-10 bg-[#197580] rounded-full flex justify-center items-center">
              <i class="pi pi-instagram" style="font-size: 1rem"></i>
            </div>
          </div>
        </div>
        <div class="flex flex-col w-full h-125 bg-white p-8 rounded-r-xl text-black">
          <h1 class="text-[32px] font-bold text-black">Kirim Pesan</h1>
          <form action="">
            <div class="flex flex-row gap-4 mt-4 text-black">
              <div class="flex flex-col w-full">
                <label for="nama" class="text-xs font-semibold uppercase text-black"
                  >Nama Lengkap</label
                >
                <input
                  type="text"
                  id="nama"
                  placeholder="John Doe"
                  class="border border-black/10 bg-black/5 rounded-md mt-1 px-2 py-1"
                />
              </div>
              <div class="flex flex-col w-full">
                <label for="email" class="text-xs font-semibold uppercase">Email</label>
                <input
                  type="email"
                  placeholder="john@example.com"
                  id="email"
                  class="border border-black/10 bg-black/5 rounded-md mt-1 px-2 py-1"
                />
              </div>
            </div>
            <div class="flex flex-col w-full mt-4">
              <label for="subjek" class="text-xs font-semibold uppercase text-black">Subjek</label>
              <input
                type="text"
                id="subjek"
                placeholder="Subjek"
                class="border border-black/10 bg-black/5 rounded-md mt-1 px-2 py-1"
              />
            </div>
            <div class="flex flex-col w-full mt-4">
              <label for="pesan" class="text-xs font-semibold uppercase text-black">Pesan</label>
              <textarea
                id="pesan"
                placeholder="Pesan"
                rows="5"
                class="border border-black/10 bg-black/5 rounded-md mt-1 px-2 py-1"
              ></textarea>
            </div>
            <button
              type="submit"
              class="bg-[#197580] text-white px-8 py-2 rounded-full text-sm font-semibold mt-10 hover:bg-[#197580]/80 transition-colors"
            >
              Kirim Pesan
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
  <FooterApp />
</template>
