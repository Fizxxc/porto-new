<template>
  <footer id="contact" class="bg-primary text-light-gray min-h-screen px-6 py-16 flex flex-col justify-center items-center relative overflow-hidden">
    <Bg :hue="0" :saturation="0" :lightness="100" class="opacity-10 absolute inset-0" />

    <div class="relative z-10 w-full max-w-5xl grid lg:grid-cols-[1fr_1.1fr] gap-8 items-start">
      <div class="space-y-6">
        <p class="uppercase tracking-[0.4em] text-sm text-light-gray/60">Get in touch</p>
        <h1 class="text-5xl lg:text-7xl font-semibold split-f">Contact.</h1>
        <p class="leading-8 text-light-gray/75">
          Open for school events, visual operation, documentation, VJ design, motion graphics, and graphic design projects.
        </p>

        <div class="grid gap-4">
          <a v-for="contact in contactDetails" :key="contact.label" :href="contact.url" target="_blank"
             class="rounded-2xl border border-light-gray/20 p-4 bg-white/5 hover:bg-white/10 transition">
            <p class="text-sm text-light-gray/50">{{ contact.label }}</p>
            <h2 class="pt-1 font-semibold">{{ contact.value }}</h2>
          </a>
        </div>
      </div>

      <form
        @submit.prevent="sendMessage"
        class="w-full bg-white/5 backdrop-blur-md rounded-3xl p-8 shadow-lg border border-light-gray/20"
      >
        <div class="flex flex-col space-y-5">
          <input
            v-model="name"
            type="text"
            placeholder="name"
            class="contact-input"
            required
          />
          <input
            v-model="email"
            type="email"
            placeholder="email"
            class="contact-input"
            required
          />
          <textarea
            v-model="message"
            placeholder="message"
            class="contact-input h-32 resize-none"
            required
          ></textarea>

          <button
            type="submit"
            class="mt-4 w-full border border-accent text-accent py-3 rounded-xl hover:bg-accent hover:text-white transition-all duration-300 font-medium"
          >
            Send via Email
          </button>
        </div>
      </form>
    </div>

    <p class="relative z-10 mt-12 text-sm text-light-gray/50 text-center">
      © {{ new Date().getFullYear() }} FizzxVerss. All rights reserved.
    </p>
  </footer>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { SplitText } from 'gsap/SplitText';
import gsap from 'gsap';
import Bg from './util/Bg.vue';

const contactDetails = [
  { label: 'Phone / WhatsApp', value: '+62 857-7656-8948', url: 'https://wa.me/6285776568948' },
  { label: 'Email', value: 'fizzx404@gmail.com', url: 'mailto:fizzx404@gmail.com' },
  { label: 'Instagram', value: '@fizzx.docx', url: 'https://instagram.com/fizzx.docx' },
  { label: 'Address', value: 'Griyayasa Blok B1/19, Cibitung, Bekasi', url: 'https://www.google.com/maps/search/?api=1&query=Griyayasa%20Blok%20B1%2F19%20Cibitung%20Bekasi' },
]

const name = ref('');
const email = ref('');
const message = ref('');

const sendMessage = () => {
  const subject = encodeURIComponent(`Portfolio message from ${name.value}`);
  const body = encodeURIComponent(`Name: ${name.value}\nEmail: ${email.value}\n\n${message.value}`);
  window.location.href = `mailto:fizzx404@gmail.com?subject=${subject}&body=${body}`;

  name.value = '';
  email.value = '';
  message.value = '';
};

onMounted(() => {
  const split = SplitText.create('.split-f', {
    type: 'words',
    mask: 'words'
  });

  gsap.from(split.words, {
    scrollTrigger: {
      trigger: '#contact',
      start: 'top bottom',
    },
    opacity: 0,
    y: 40,
    duration: 1,
    stagger: 0.1,
    ease: 'power3.out',
  });
});
</script>

<style scoped>
.bg-primary {
  background-color: #0f0f10;
}
.text-light-gray {
  color: #e0e0e0;
}
.text-accent {
  color: #a855f7;
}
.border-accent {
  border-color: #a855f7;
}
.hover\:bg-accent:hover {
  background-color: #a855f7;
}
.contact-input {
  width: 100%;
  background-color: rgba(168, 85, 247, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  color: #e0e0e0;
  padding: 12px 16px;
  border-radius: 12px;
  font-size: 1rem;
  outline: none;
  transition: all 0.3s;
}
.contact-input::placeholder {
  color: rgba(255, 255, 255, 0.5);
}
.contact-input:focus {
  border-color: #a855f7;
  box-shadow: 0 0 10px #a855f755;
}
</style>
