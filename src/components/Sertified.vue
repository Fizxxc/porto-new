<template>
  <section class="px-4 lg:px-16 py-10 lg:py-24 min-h-screen bg-primary text-soft-ivory">
    <div class="flex flex-col gap-y-10">
      <div class="flex flex-col gap-y-3">
        <p class="uppercase tracking-[0.4em] text-sm text-soft-ivory/60">Certificates</p>
        <h1 class="text-5xl lg:text-8xl">Sertifikat</h1>
        <p class="max-w-3xl leading-8 text-soft-ivory/80">
          Bagian ini sudah dibuat khusus untuk menampilkan gambar sertifikat. File PDF yang diberikan sudah dirender
          menjadi <span class="font-semibold text-soft-ivory">sertifikat1.jpg</span>. Untuk mengganti dummy, cukup
          timpa file dengan nama yang sama di folder <span class="font-semibold text-soft-ivory">src/assets/img/sertified</span>.
        </p>
      </div>

      <div class="grid gap-6 md:grid-cols-2 xl:grid-cols-3">
        <article v-for="certificate in certificates" :key="certificate.filename" class="group rounded-3xl overflow-hidden bg-white text-primary shadow-lg">
          <a :href="certificate.image" target="_blank" class="block overflow-hidden bg-soft-ivory">
            <img :src="certificate.image" :alt="certificate.title" class="aspect-[16/11] w-full object-cover transition duration-500 group-hover:scale-105" />
          </a>
          <div class="p-5 space-y-2">
            <div class="flex items-center justify-between gap-4">
              <h2 class="text-xl font-semibold">{{ certificate.title }}</h2>
              <span class="rounded-full bg-soft-ivory px-3 py-1 text-xs">{{ certificate.filename }}</span>
            </div>
            <p class="text-sm text-primary/70">{{ certificate.description }}</p>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
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
    description: 'Hasil render dari PDF sertifikat Maheswara Hafiz.',
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
</script>
