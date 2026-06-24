<template>
  <section id="certificates" class="relative min-h-svh overflow-hidden bg-primary text-soft-ivory">
    <Bg :hue="0" :saturation="0" :lightness="100" class="pointer-events-none absolute inset-0 opacity-10" />

    <div class="section-shell relative z-10">
      <div class="grid gap-6 lg:grid-cols-[1fr_0.78fr] lg:items-end">
        <div class="space-y-4">
          <p class="section-kicker text-soft-ivory/60">Certificates</p>
          <h1 class="fluid-title safe-text">Sertifikat</h1>
          <p class="max-w-3xl text-base leading-8 text-soft-ivory/75 sm:text-lg safe-text">
            Semua sertifikat ditampilkan dalam card grid sederhana supaya lebih stabil, rapi, dan tetap nyaman dilihat di mobile, tablet, maupun desktop.
          </p>
        </div>

        <div class="rounded-[1.75rem] border border-white/12 bg-white/8 p-5 shadow-xl backdrop-blur-md sm:p-6">
          <div class="flex items-start gap-4">
            <span class="flex h-12 w-12 shrink-0 items-center justify-center rounded-2xl bg-soft-ivory text-xl text-primary">
              <i class="pi pi-folder-open"></i>
            </span>
            <div class="min-w-0 space-y-2">
              <h2 class="text-xl font-semibold safe-text">Cara ganti file</h2>
              <p class="text-sm leading-6 text-soft-ivory/70 safe-text">
                Timpa file di folder <span class="font-semibold text-white">src/assets/img/sertified/</span> dengan nama yang sama, contohnya <span class="font-semibold text-white">sertifikat2.jpg</span>.
              </p>
            </div>
          </div>
        </div>
      </div>

      <div class="mt-10 grid gap-5 sm:grid-cols-2 xl:grid-cols-3">
        <article v-for="certificate in certificates" :key="certificate.filename"
          class="certificate-card group flex min-w-0 flex-col overflow-hidden rounded-[1.75rem] border border-white/12 bg-white/8 p-3 shadow-xl backdrop-blur-md transition duration-300 hover:-translate-y-1 hover:bg-white/12">
          <a :href="certificate.image" target="_blank" rel="noopener noreferrer"
            class="block overflow-hidden rounded-[1.25rem] bg-white p-2">
            <img :src="certificate.image" :alt="certificate.title"
              class="aspect-[16/11] w-full object-contain transition duration-500 group-hover:scale-[1.02]" />
          </a>

          <div class="flex flex-1 flex-col gap-4 p-4">
            <div class="min-w-0 space-y-2">
              <div class="flex flex-wrap items-start justify-between gap-3">
                <h2 class="text-xl font-semibold leading-tight safe-text">{{ certificate.title }}</h2>
                <span class="rounded-full bg-soft-ivory/12 px-3 py-1 text-xs text-soft-ivory/70 safe-text">
                  {{ certificate.filename }}
                </span>
              </div>
              <p class="text-sm leading-6 text-soft-ivory/68 safe-text">{{ certificate.description }}</p>
            </div>

            <a :href="certificate.image" target="_blank" rel="noopener noreferrer"
              class="mt-auto inline-flex w-full items-center justify-center gap-2 rounded-2xl bg-soft-ivory px-4 py-3 text-sm font-semibold text-primary transition hover:bg-white">
              Lihat gambar
              <i class="pi pi-arrow-up-right text-xs"></i>
            </a>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
import Bg from './util/Bg.vue'
import sertifikat1 from '@/assets/img/sertified/sertifikat1.jpg'
import sertifikat2 from '@/assets/img/sertified/sertifikat2.jpg'
import sertifikat3 from '@/assets/img/sertified/sertifikat3.jpg'
import sertifikat4 from '@/assets/img/sertified/sertifikat4.jpg'
import sertifikat5 from '@/assets/img/sertified/sertifikat5.jpg'
import sertifikat6 from '@/assets/img/sertified/sertifikat6.jpg'

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
    description: 'Dummy certificate. Ganti file ini dengan sertifikat asli.',
    image: sertifikat2,
  },
  {
    title: 'Sertifikat 3',
    filename: 'sertifikat3.jpg',
    description: 'Dummy certificate. Ganti file ini dengan sertifikat asli.',
    image: sertifikat3,
  },
  {
    title: 'Sertifikat 4',
    filename: 'sertifikat4.jpg',
    description: 'Dummy certificate. Ganti file ini dengan sertifikat asli.',
    image: sertifikat4,
  },
  {
    title: 'Sertifikat 5',
    filename: 'sertifikat5.jpg',
    description: 'Dummy certificate. Ganti file ini dengan sertifikat asli.',
    image: sertifikat5,
  },
  {
    title: 'Sertifikat 6',
    filename: 'sertifikat6.jpg',
    description: 'Dummy certificate. Ganti file ini dengan sertifikat asli.',
    image: sertifikat6,
  },
]
</script>

<style scoped>
.certificate-card {
  contain: layout paint;
}
</style>
