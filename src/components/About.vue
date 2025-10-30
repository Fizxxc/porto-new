<template>
  <section class="p-4 lg:px-16 py-10 lg:py-24 min-h-screen">
    <div class="flex flex-col gap-y-6 gap-x-20 py-2 md:flex-row lg:justify-between" id="about-wrapper">
      <!-- Text Section -->
      <div class="grid lg:grid-rows-2 gap-2">
        <h1 class="text-5xl w-full py-2 lg:text-8xl self-center ">About Me</h1>
        <p class="lg:indent-4 text-justify">
          As an 11th-grade Visual Communication Design student, I am deeply interested in the <span
            class="font-bold">creative world and how an image can tell a story</span>. I spend much of my time honing my
          graphic design skills, especially creating logos, posters, and social media content using <span
            class="font-bold">Adobe Photoshop and Illustrator</span>. I also enjoy experimenting with <span
            class="font-bold">hand sketches and photography</span> as sources of inspiration. I want to keep growing as
          a designer, learn from professionals, and someday take part in real, exciting, and impactful projects.
        </p>
      </div>

      <!-- Image Section -->
      <div
        class="h-80 w-full overflow-hidden border border-primary relative group  md:w-80 lg:w-1/2 lg:h-[500px] md:shrink-0 blob"
        id="img-wrapper">
        <img src="@/assets/img/me.jpg" alt="profile-image" />
      </div>
    </div>
  </section>
</template>

<script setup>
import gsap from 'gsap';
import ScrollTrigger from 'gsap/ScrollTrigger';
import { onMounted, ref } from 'vue';

const isTouched = ref(false); // digunakan untuk menyentuh di mobile

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
