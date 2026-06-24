<template>
  <section class="section-shell min-h-svh">
    <div class="grid gap-10 xl:grid-cols-[1.05fr_0.95fr] xl:items-center" id="about-wrapper">
      <div class="flex flex-col gap-y-7">
        <div class="space-y-4">
          <p class="section-kicker text-warm-gray">About Me</p>
          <h1 class="fluid-title max-w-5xl py-2 safe-text">Visual Communication Design Student</h1>
          <p class="max-w-3xl text-base sm:text-lg leading-8 text-justify safe-text">
            I am a Visual Communication Design (VCD) student at Metland Vocational School with a strong interest in
            <span class="font-bold">motion graphics, graphic design, VJ design, and sound operation</span>. I enjoy
            transforming simple shapes, such as boxes and circles, into engaging and meaningful animations.
          </p>
          <p class="max-w-3xl text-base sm:text-lg leading-8 text-justify safe-text">
            I am adaptable, enjoy challenges, and always strive to deliver high-quality results through both independent
            work and effective teamwork.
          </p>
        </div>

        <div class="grid gap-4 sm:grid-cols-2">
          <div v-for="detail in personalDetails" :key="detail.label" class="rounded-3xl border border-primary/10 bg-white/70 p-5 shadow-sm">
            <p class="text-xs sm:text-sm uppercase tracking-widest text-warm-gray safe-text">{{ detail.label }}</p>
            <h3 class="pt-2 font-semibold text-base sm:text-lg safe-text">{{ detail.value }}</h3>
          </div>
        </div>

        <div class="rounded-[2rem] bg-primary text-soft-ivory p-6 sm:p-8 shadow-xl">
          <h2 class="text-2xl sm:text-3xl font-semibold mb-5">Education</h2>
          <div class="space-y-5">
            <div v-for="edu in education" :key="edu.period" class="border-l border-soft-ivory/40 pl-4">
              <p class="text-sm text-soft-ivory/70 safe-text">{{ edu.period }}</p>
              <h3 class="font-semibold text-lg safe-text">{{ edu.school }}</h3>
              <p class="text-soft-ivory/80 safe-text">{{ edu.detail }}</p>
            </div>
          </div>
        </div>
      </div>

      <div
        class="h-[22rem] sm:h-[30rem] xl:h-[40rem] w-full overflow-hidden border border-primary/15 relative group shadow-2xl blob bg-white"
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
  const clamp = gsap.utils.clamp(-8, 8);

  ScrollTrigger.create({
    trigger: '#img-wrapper',
    onUpdate: (self) => {
      const velocity = self.getVelocity();
      skewSetter(clamp(velocity / -260));
    },
  });
});
</script>

<style scoped>
.blob {
  animation: blobMorph 8s ease-in-out infinite;
}

@media (max-width: 767px) {
  .blob {
    border-radius: 2rem !important;
    animation: none;
  }
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
