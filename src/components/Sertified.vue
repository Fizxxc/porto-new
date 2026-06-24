<template>
  <section class="relative min-h-svh overflow-hidden bg-primary text-soft-ivory">
    <Bg :hue="0" :saturation="0" :lightness="100" class="pointer-events-none absolute inset-0 opacity-10" />
    <div class="section-shell relative z-10">
      <div class="grid gap-10 xl:grid-cols-[0.9fr_1.1fr] xl:items-center">
        <div class="space-y-7">
          <div class="space-y-4">
            <p class="section-kicker text-soft-ivory/60">Certificates</p>
            <h1 class="fluid-title safe-text">Sertifikat</h1>
            <p class="max-w-2xl leading-8 text-soft-ivory/75 safe-text">
              Area ini memakai konsep kartu bertumpuk dengan efek glassmorphism. File sertifikat asli dari PDF sudah
              ditampilkan sebagai <span class="font-semibold text-white">sertifikat1.jpg</span>; file dummy lainnya bisa langsung diganti dengan nama yang sama.
            </p>
          </div>

          <div class="glass-panel rounded-[2rem] p-5 sm:p-6">
            <p class="text-sm uppercase tracking-[0.25em] text-soft-ivory/50">Cara mengganti</p>
            <p class="pt-3 leading-7 text-soft-ivory/80 safe-text">
              Simpan gambar baru ke folder <span class="font-semibold text-white">src/assets/img/sertified/</span>, lalu timpa
              <span class="font-semibold text-white">sertifikat2.jpg</span>, <span class="font-semibold text-white">sertifikat3.jpg</span>, dan seterusnya.
            </p>
          </div>
        </div>

        <div class="relative min-h-[34rem] sm:min-h-[39rem]">
          <button v-for="(certificate, index) in featuredStack" :key="`${certificate.filename}-${index}`" type="button"
            class="certificate-stack-card glass-panel absolute left-1/2 top-1/2 w-[min(92vw,25rem)] -translate-x-1/2 -translate-y-1/2 overflow-hidden rounded-[2rem] p-3 text-left transition-all duration-500 hover:-translate-y-[52%] focus:outline-none focus:ring-2 focus:ring-white/60"
            :style="stackStyle(index)" @click="nextCertificate" :aria-label="`Lihat ${certificate.title}`">
            <img :src="certificate.image" :alt="certificate.title" class="aspect-[16/11] w-full rounded-[1.35rem] object-cover bg-white" />
            <div class="space-y-2 p-4">
              <div class="flex flex-wrap items-center justify-between gap-2">
                <h2 class="text-xl font-semibold safe-text">{{ certificate.title }}</h2>
                <span class="rounded-full bg-white/10 px-3 py-1 text-xs text-soft-ivory/70 safe-text">{{ certificate.filename }}</span>
              </div>
              <p class="text-sm leading-6 text-soft-ivory/70 safe-text">{{ certificate.description }}</p>
            </div>
          </button>
        </div>
      </div>

      <div class="mt-8 grid gap-4 sm:grid-cols-2 lg:grid-cols-3">
        <article v-for="(certificate, index) in certificates" :key="certificate.filename"
          class="glass-panel group overflow-hidden rounded-[1.75rem] p-3 transition duration-300 hover:-translate-y-1"
          :class="activeIndex === index ? 'ring-2 ring-white/50' : ''">
          <button type="button" class="block w-full overflow-hidden rounded-[1.25rem] bg-white text-left" @click="selectCertificate(index)">
            <img :src="certificate.image" :alt="certificate.title" class="aspect-[16/11] w-full object-cover transition duration-500 group-hover:scale-105" />
          </button>
          <div class="p-4">
            <div class="flex flex-wrap items-center justify-between gap-3">
              <h2 class="text-lg font-semibold safe-text">{{ certificate.title }}</h2>
              <a :href="certificate.image" target="_blank" rel="noopener noreferrer"
                class="inline-flex h-9 w-9 shrink-0 items-center justify-center rounded-full bg-white/10 text-soft-ivory transition hover:bg-white hover:text-primary"
                :aria-label="`Buka ${certificate.title}`">
                <i class="pi pi-arrow-up-right"></i>
              </a>
            </div>
            <p class="pt-2 text-xs text-soft-ivory/50 safe-text">{{ certificate.filename }}</p>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
import { computed, ref } from 'vue'
import Bg from './util/Bg.vue'
import sertifikat1 from '@/assets/img/sertified/sertifikat1.jpg'
import sertifikat2 from '@/assets/img/sertified/sertifikat2.jpg'
import sertifikat3 from '@/assets/img/sertified/sertifikat3.jpg'
import sertifikat4 from '@/assets/img/sertified/sertifikat4.jpg'
import sertifikat5 from '@/assets/img/sertified/sertifikat5.jpg'
import sertifikat6 from '@/assets/img/sertified/sertifikat6.jpg'

const activeIndex = ref(0)

const certificates = [
  {
    title: 'Sertifikat Penghargaan',
    filename: 'sertifikat1.jpg',
    description: 'Render gambar dari PDF sertifikat Maheswara Hafiz.',
    image: sertifikat1,
  },
  {
    title: 'Sertifikat 2',
    filename: 'sertifikat2.jpg',
    description: 'Dummy certificate - ganti file ini dengan sertifikat asli.',
    image: sertifikat2,
  },
  {
    title: 'Sertifikat 3',
    filename: 'sertifikat3.jpg',
    description: 'Dummy certificate - ganti file ini dengan sertifikat asli.',
    image: sertifikat3,
  },
  {
    title: 'Sertifikat 4',
    filename: 'sertifikat4.jpg',
    description: 'Dummy certificate - ganti file ini dengan sertifikat asli.',
    image: sertifikat4,
  },
  {
    title: 'Sertifikat 5',
    filename: 'sertifikat5.jpg',
    description: 'Dummy certificate - ganti file ini dengan sertifikat asli.',
    image: sertifikat5,
  },
  {
    title: 'Sertifikat 6',
    filename: 'sertifikat6.jpg',
    description: 'Dummy certificate - ganti file ini dengan sertifikat asli.',
    image: sertifikat6,
  },
]

const featuredStack = computed(() => {
  return [0, 1, 2].map((offset) => certificates[(activeIndex.value + offset) % certificates.length])
})

const selectCertificate = (index) => {
  activeIndex.value = index
}

const nextCertificate = () => {
  activeIndex.value = (activeIndex.value + 1) % certificates.length
}

const stackStyle = (index) => {
  const styles = [
    { transform: 'translate(-50%, -50%) rotate(-2deg)', zIndex: 30, opacity: 1 },
    { transform: 'translate(calc(-50% + 34px), calc(-50% + 34px)) rotate(4deg)', zIndex: 20, opacity: 0.82 },
    { transform: 'translate(calc(-50% + 68px), calc(-50% + 68px)) rotate(8deg)', zIndex: 10, opacity: 0.58 },
  ]

  return styles[index]
}
</script>

<style scoped>
.certificate-stack-card {
  transform-origin: center;
}

@media (max-width: 479px) {
  .certificate-stack-card {
    width: min(86vw, 22rem);
  }
}
</style>
