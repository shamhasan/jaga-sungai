<script lang="ts" setup>
import { ref } from 'vue'
import InputText from 'primevue/inputtext'
import RadioButton from 'primevue/radiobutton'
import { Button } from 'primevue'
import ToggleSwitch from 'primevue/toggleswitch'

const props = defineProps<{
  isLaporMode: boolean
  isLaporVisible: boolean
}>()

const selectedValue = ref('1')
const checked = ref(false)
</script>

<template>
  <Transition
    enter-active-class="transition duration-300 ease-out"
    enter-from-class="transform opacity-0 -translate-x-10"
    enter-to-class="transform opacity-100 translate-x-0"
    leave-active-class="transition duration-200 ease-in"
    leave-from-class="transform opacity-100 translate-x-0"
    leave-to-class="transform opacity-0 -translate-x-10"
  >
    <div
      v-if="props.isLaporMode"
      class="absolute top-36 left-12 right-12 z-[700] p-4 flex items-center justify-center w-1/4 flex-col gap-4 transition-all! duration-300! ease-in-out!"
    >
      <Button
        class="bg-[url(../assets/images/bg-button-lapor.png)]! bg-fit! bg-top! bg-no-repeat! rounded-xl! px-4! py-4! cursor-pointer! w-full! flex! items-center! justify-center!"
        @click="$emit('toggleLaporVisible')"
      >
        <h4 class="font-bold text-white text-md uppercase">Laporkan Pencemaran sungai</h4>
      </Button>

      <Transition
        enter-active-class="transition duration-300 ease-out"
        enter-from-class="transform opacity-0 scale-95 -translate-y-4"
        enter-to-class="transform opacity-100 scale-100 translate-y-0"
        leave-active-class="transition duration-200 ease-in"
        leave-from-class="transform opacity-100 scale-100 translate-y-0"
        leave-to-class="transform opacity-0 scale-95 -translate-y-4"
      >
        <div
          class="flex flex-col justify-center items-start w-full h-full p-6 bg-white rounded-md gap-1"
          v-if="props.isLaporVisible"
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
          <p class="text-black uppercase font-semibold text-xs mt-1 text-left">Tingkat keparahan</p>
          <div class="relative w-full">
            <div
              class="bg-[url(../assets/images/level-indikator.png)] bg-no-repeat w-full h-2 rounded-md"
              style="background-size: cover; background-position: center"
            ></div>
            <div class="flex flex-row justify-between items-center w-full pt-2">
              <RadioButton
                v-model="selectedValue"
                value="1"
                :pt="{
                  box: { class: 'bg-white! border-1 border-[#075158]!' },
                  icon: { class: 'bg-[#075158]!' },
                }"
              />
              <RadioButton
                v-model="selectedValue"
                value="2"
                :pt="{
                  box: { class: 'bg-white! border-1 border-[#075158]!' },
                  icon: { class: 'bg-[#075158]!' },
                }"
              />
              <RadioButton
                v-model="selectedValue"
                value="3"
                :pt="{
                  box: { class: 'bg-white! border-1 border-[#075158]!' },
                  icon: { class: 'bg-[#075158]!' },
                }"
              />
              <RadioButton
                v-model="selectedValue"
                value="4"
                :pt="{
                  box: { class: 'bg-white! border-1 border-[#075158]!' },
                  icon: { class: 'bg-[#075158]!' },
                }"
              />
              <RadioButton
                v-model="selectedValue"
                value="5"
                :pt="{
                  box: { class: 'bg-white! border-1 border-[#075158]!' },
                  icon: { class: 'bg-[#075158]!' },
                }"
              />
            </div>
          </div>
          <div class="flex flex-row justify-between items-center w-full">
            <p class="text-black font-regular text-xs text-left">Rendah</p>
            <p class="text-black font-regular text-xs text-left">Kritis</p>
          </div>
          <div class="flex w-full mt-2">
            <p class="text-black uppercase font-semibold text-xs text-left">Kategori Sampah</p>
          </div>
          <div class="flex flex-row w-full mt-1 justify-start gap-2">
            <Button
              class="bg-white! border! border-black/40! py-1! px-2! rounded-md! text-[11px]! text-black/60! uppercase! cursor-pointer! hover:bg-[#046C69]! hover:text-white! transition-all!"
            >
              Plastik
            </Button>
            <Button
              class="bg-white! border! border-black/40! py-1! px-2! rounded-md! text-[11px]! text-black/60! uppercase! cursor-pointer! hover:bg-[#046C69]! hover:text-white! transition-all!"
            >
              kimia
            </Button>
            <Button
              class="bg-white! border! border-black/40! py-1! px-2! rounded-md! text-[11px]! text-black/60! uppercase! cursor-pointer! hover:bg-[#046C69]! hover:text-white! transition-all!"
            >
              limbah
            </Button>
            <Button
              class="bg-white! border! border-black/40! py-1! px-2! rounded-md! text-[11px]! text-black/60! uppercase! cursor-pointer! hover:bg-[#046C69]! hover:text-white! transition-all!"
            >
              organik
            </Button>
          </div>
          <div
            class="flex flex-row w-full mt-1 h-full cursor-pointer bg-black/5 border-black/40 rounded-md justify-center items-center p-4 border-dashed border-2"
          >
            <i class="pi pi-image text-black/70 mx-2" style="font-size: 1.5rem"></i>
            <div class="flex flex-col w-fit h-full justify-start items-start">
              <p class="text-[#046C69] font-semibold text-xs-semibold text-xs text-left">
                Klik atau drag foto kesini
              </p>
              <p class="text-black/70 font-regular text-xs text-left">JPEG, PNG | Max 2MB</p>
            </div>
          </div>
          <p class="text-black uppercase font-semibold text-xs text-left mt-2">
            Observasi (Optional)
          </p>
          <Textarea
            placeholder="Tuliskan Keterangan Tambahan"
            class="w-full pl-3! pr-10! py-2! rounded-md! border-black/20! bg-black/10! text-xs! font-regular! text-black/80! focus:text-black! border! outline-none! h-23! resize-none focus:border-black/70! focus:outline-none!"
          />
          <div class="flex flex-row justify-between items-center mt-2 w-full h-full text-black">
            <p class="text-black uppercase font-semibold text-xs text-left mt-2">
              Kirim sebagai anonim
            </p>
            <ToggleSwitch
              v-model="checked"
              :pt="{
                root: { class: 'w-9! h-5!' },
                slider: {
                  class: ['before:w-3! before:h-3!', checked ? 'bg-[#4FC4C4]!' : 'bg-black/20!'],
                },
                handle: {
                  class: checked ? 'bg-white!' : 'bg-black/20!',
                },
              }"
            />
          </div>
          <Button
            class="bg-[#075158]! w-full h-full py-2! rounded-md! text-sm! text-white! mt-2 uppercase! cursor-pointer! hover:bg-[#046C69]! font-regular! transition-all!"
          >
            Kirim Laporan
          </Button>
        </div>
      </Transition>
    </div>
  </Transition>
</template>
