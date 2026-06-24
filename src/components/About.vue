<template>
  <section class="p-4 lg:px-16 py-10 lg:py-24 min-h-screen">
    <div class="flex flex-col gap-y-10 gap-x-20 py-2 md:flex-row lg:justify-between" id="about-wrapper">
      <div class="flex flex-col gap-y-8 lg:w-1/2">
        <div class="space-y-4">
          <p class="uppercase tracking-[0.4em] text-sm text-warm-gray">About Me</p>
          <h1 class="text-5xl w-full py-2 lg:text-8xl self-center">Visual Communication Design Student</h1>
          <p class="lg:indent-4 text-justify leading-8">
            I am a Visual Communication Design (VCD) student at Metland Vocational School with a strong interest in
            <span class="font-bold">motion graphics, graphic design, VJ design, and sound operation</span>. I enjoy
            transforming simple shapes, such as boxes and circles, into engaging and meaningful animations.
          </p>
          <p class="text-justify leading-8">
            I am adaptable, enjoy challenges, and always strive to deliver high-quality results through both independent
            work and effective teamwork.
          </p>
        </div>

        <div class="grid sm:grid-cols-2 gap-4">
          <div v-for="detail in personalDetails" :key="detail.label" class="rounded-2xl border border-primary/10 bg-white/60 p-5">
            <p class="text-sm uppercase tracking-widest text-warm-gray">{{ detail.label }}</p>
            <h3 class="pt-2 font-semibold text-lg">{{ detail.value }}</h3>
          </div>
        </div>

        <div class="rounded-2xl bg-primary text-soft-ivory p-6">
          <h2 class="text-2xl font-semibold mb-4">Education</h2>
          <div class="space-y-5">
            <div v-for="edu in education" :key="edu.period" class="border-l border-soft-ivory/40 pl-4">
              <p class="text-sm text-soft-ivory/70">{{ edu.period }}</p>
              <h3 class="font-semibold text-lg">{{ edu.school }}</h3>
              <p class="text-soft-ivory/80">{{ edu.detail }}</p>
            </div>
          </div>
        </div>
      </div>

      <div
        class="h-80 w-full overflow-hidden border border-primary relative group md:w-80 lg:w-1/2 lg:h-[620px] md:shrink-0 blob"
        id="img-wrapper">
        <img src="@/assets/img/me.jpg" alt="Hafiz Al Fariz profile" class="w-full h-full object-cover object-top" />
      </div>
    </div>
  </section>
</template>

<script setup>
import gsap from 'gsap';
import ScrollTrigger from 'gsap/ScrollTrigger';
import { onMounted } from 'vue';

const personalDetails = [
  { label: 'Based in', value: 'Cibitung, Bekasi' },
  { label: 'Birth date', value: 'January 14, 2009' },
  { label: 'Major', value: 'Visual Communication Design' },
  { label: 'Height / Weight', value: '170cm / 62kg' },
]

const education = [
  {
    period: '2024 - Present',
    school: 'Metland Vocational School Cibitung, Bekasi',
    detail: 'Major: Visual Communication Design',
  },
  {
    period: '2021 - 2024',
    school: 'SMP Negeri 5 Cibitung, Bekasi',
    detail: 'Junior High School',
  },
  {
    period: '2015 - 2021',
    school: 'SD Negeri Wanasari 12 Cibitung, Bekasi',
    detail: 'Elementary School',
  },
]

gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
  const skewSetter = gsap.quickTo('#img-wrapper', 'skewY');
  const clamp = gsap.utils.clamp(-10, 10);

  ScrollTrigger.create({
    trigger: '#img-wrapper',
    onUpdate: (self) => {
      const velocity = self.getVelocity();
      skewSetter(clamp(velocity / -200));
    },
  });
});
</script>

<style scoped>
.blob {
  animation: blobMorph 8s ease-in-out infinite;
}

@keyframes blobMorph {
  0% {
    border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%;
  }

  50% {
    border-radius: 30% 60% 70% 40% / 50% 60% 30% 60%;
  }

  100% {
    border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%;
  }
}
</style>
