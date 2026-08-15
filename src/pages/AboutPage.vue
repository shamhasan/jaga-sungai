<script setup lang="ts">
import AboutComponent from '../components/AboutComponent.vue'
</script>

<template>
  <section>
    <div
      class="relative w-full h-full flex flex-col items-start justify-center p-8 bg-[#0F2E2E] overflow-hidden"
    >
      <div class="absolute inset-0 w-full h-full">
        <img
          src="../assets/images/Beranda.webp"
          alt="Background"
          class="w-full h-full object-cover object-top blur-1 opacity-80 -z-10"
        />
      </div>
      <div
        class="relative flex flex-col w-full text-white justify-center items-center mt-25 mb-5 z-30"
      >
        <h1 class="text-white text-[60px] font-bold">Tentang Jaga Sungai</h1>
        <p>Bersama Memulihkan Nadi Kehidupan</p>
      </div>
    </div>
  </section>
  <section>
    <div
      class="flex flex-col justify-center items-start bg-white text-black w-full h-full px-42 pt-12 pb-12 z-20"
    >
      <div class="flex flex-row gap-8 p-4 justify-start items-center">
        <h1 class="text-[32px] font-bold w-1/3 shrink-0 leading-10">
          Inisiatif Kolaboratif <br />
          <span class="text-[#006672]">untuk Sungai Indonesia</span>
        </h1>
        <p class="text-md color-[#3E494B] font-regular max-w-xl">
          JagaSungai lahir dari keprihatinan mendalam terhadap kondisi ekosistem perairan darat
          kita. Kami percaya bahwa setiap tetes air bersih adalah hak, dan setiap sungai yang sehat
          adalah warisan yang harus dijaga untuk generasi mendatang.
        </p>
        <p class="text-md color-[#3E494B] font-regular max-w-xl">
          Melalui platform ini, kami menjembatani masyarakat, pemerintah, dan pemerhati lingkungan
          untuk berkolaborasi secara transparan, melaporkan kondisi sungai secara real-time, dan
          mengorganisir aksi pemulihan yang terukur dan berdampak nyata.
        </p>
      </div>
    </div>

    <div class="flex justify-center items-center px-84">
      <h1 class="text-[46px] font-semibold text-center text-[#006672] py-12 leading-14">
        <span class="hover:bg-[#006672] rounded-xl hover:text-white px-2">Beyond the drive</span>
        <span class="hover:bg-[#006672] rounded-xl hover:text-white px-2">we provide an</span>
        <br />
        <span class="hover:bg-[#006672] rounded-xl hover:text-white px-2"
          >ecosystem of support</span
        >
        <span class="hover:bg-[#006672] rounded-xl hover:text-white px-2">and luxury</span> <br />
        <span class="hover:bg-[#006672] rounded-xl hover:text-white px-2">designed around</span>
        <span class="hover:bg-[#006672] rounded-xl hover:text-white px-2">your life.</span>
      </h1>
    </div>

    <div class="flex justify-center items-center flex-row px-42 py-12 gap-8">
      <AboutComponent
        title="Transparansi Data"
        description="Pemantauan dan pelaporan kondisi kualitas air berbasis komunitas yang terbuka untuk publik."
        icon="map-marker"
      />
      <AboutComponent
        title="Transparansi Data"
        description="Pemantauan dan pelaporan kondisi kualitas air berbasis komunitas yang terbuka untuk publik."
        icon="map-marker"
      />
      <AboutComponent
        title="Transparansi Data"
        description="Pemantauan dan pelaporan kondisi kualitas air berbasis komunitas yang terbuka untuk publik."
        icon="map-marker"
      />
    </div>
  </section>
  <div class="w-full"></div>
</template>
