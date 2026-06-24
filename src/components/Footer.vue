<template>
  <footer id="contact" class="relative min-h-svh overflow-hidden bg-primary text-light-gray">
    <Bg :hue="0" :saturation="0" :lightness="100" class="pointer-events-none absolute inset-0 opacity-10" />

    <div class="section-shell relative z-10 flex min-h-svh flex-col justify-center gap-10 pb-28 md:pb-16">
      <div class="grid gap-6 xl:grid-cols-[0.9fr_1.1fr] xl:items-stretch">
        <section class="rounded-[2rem] border border-white/12 bg-white/8 p-5 shadow-xl backdrop-blur-md sm:p-8">
          <p class="section-kicker text-light-gray/60">Get in touch</p>
          <h1 class="fluid-title pt-4 font-semibold split-f safe-text">Contact.</h1>
          <p class="max-w-xl pt-5 text-base leading-8 text-light-gray/75 sm:text-lg safe-text">
            Terbuka untuk kebutuhan event sekolah, visual operation, dokumentasi, VJ design, motion graphics, dan graphic design.
          </p>

          <div class="mt-7 grid gap-3">
            <a v-for="contact in contactDetails" :key="contact.label" :href="contact.url" target="_blank" rel="noopener noreferrer"
              class="group flex min-w-0 items-center gap-4 rounded-2xl border border-light-gray/12 bg-primary/30 p-4 transition hover:-translate-y-1 hover:border-soft-ivory/40 hover:bg-white/10">
              <span class="flex h-11 w-11 shrink-0 items-center justify-center rounded-full bg-soft-ivory text-xl text-primary transition group-hover:bg-white">
                <i :class="contact.icon"></i>
              </span>
              <span class="min-w-0 flex-1">
                <span class="block text-xs uppercase tracking-[0.2em] text-light-gray/45 safe-text">{{ contact.label }}</span>
                <span class="block pt-1 font-semibold leading-snug text-light-gray safe-text">{{ contact.value }}</span>
              </span>
              <i class="pi pi-arrow-up-right hidden shrink-0 text-light-gray/35 transition group-hover:text-light-gray sm:block"></i>
            </a>
          </div>
        </section>

        <form @submit.prevent="sendMessage" class="rounded-[2rem] border border-white/12 bg-white/8 p-5 shadow-xl backdrop-blur-md sm:p-8">
          <div class="flex h-full flex-col gap-5">
            <div class="rounded-[1.5rem] border border-light-gray/10 bg-primary/25 p-5">
              <p class="text-sm uppercase tracking-[0.25em] text-light-gray/45 safe-text">Quick Message</p>
              <h2 class="pt-3 text-2xl font-semibold sm:text-3xl safe-text">Send a message via email</h2>
              <p class="pt-3 text-sm leading-6 text-light-gray/58 safe-text">
                Isi form ini akan otomatis masuk ke email supaya lebih gampang dikirim.
              </p>
            </div>

            <div class="grid gap-4 sm:grid-cols-2">
              <label class="space-y-2">
                <span class="text-sm text-light-gray/60">Name</span>
                <input v-model="name" type="text" placeholder="Your name" class="contact-input" required />
              </label>
              <label class="space-y-2">
                <span class="text-sm text-light-gray/60">Email</span>
                <input v-model="email" type="email" placeholder="your@email.com" class="contact-input" required />
              </label>
            </div>

            <label class="flex flex-1 flex-col space-y-2">
              <span class="text-sm text-light-gray/60">Message</span>
              <textarea v-model="message" placeholder="Tell me about your event or project..." class="contact-input min-h-40 flex-1 resize-none" required></textarea>
            </label>

            <button type="submit"
              class="mt-2 inline-flex w-full items-center justify-center gap-3 rounded-2xl bg-soft-ivory px-5 py-4 font-semibold text-primary transition hover:-translate-y-1 hover:bg-white">
              Send via Email
              <i class="pi pi-send"></i>
            </button>
          </div>
        </form>
      </div>

      <div class="flex flex-col gap-3 text-center text-sm text-light-gray/50 sm:flex-row sm:items-center sm:justify-between sm:text-left">
        <p class="safe-text">© {{ new Date().getFullYear() }} FizzxVerss. All rights reserved.</p>
        <p class="safe-text">Hafiz Al Fariz — Visual Communication Design</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { SplitText } from 'gsap/SplitText';
import ScrollTrigger from 'gsap/ScrollTrigger';
import gsap from 'gsap';
import Bg from './util/Bg.vue';

gsap.registerPlugin(ScrollTrigger);

const contactDetails = [
  { label: 'WhatsApp', icon: 'pi pi-whatsapp', value: '+62 857-7656-8948', url: 'https://wa.me/6285776568948' },
  { label: 'Email', icon: 'pi pi-at', value: 'fizzx404@gmail.com', url: 'mailto:fizzx404@gmail.com' },
  { label: 'Instagram', icon: 'pi pi-instagram', value: '@fizzx.docx', url: 'https://instagram.com/fizzx.docx' },
  { label: 'Address', icon: 'pi pi-map-marker', value: 'Griyayasa Blok B1/19, Cibitung, Bekasi', url: 'https://www.google.com/maps/search/?api=1&query=Griyayasa%20Blok%20B1%2F19%20Cibitung%20Bekasi' },
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
.contact-input {
  width: 100%;
  min-width: 0;
  background-color: rgba(0, 0, 0, 0.22);
  border: 1px solid rgba(255, 255, 255, 0.16);
  color: #e0e0e0;
  padding: 0.9rem 1rem;
  border-radius: 1rem;
  font-size: 1rem;
  outline: none;
  transition: border-color 0.3s, box-shadow 0.3s, background-color 0.3s;
}
.contact-input::placeholder {
  color: rgba(255, 255, 255, 0.36);
}
.contact-input:focus {
  background-color: rgba(255, 255, 255, 0.08);
  border-color: rgba(234, 228, 213, 0.75);
  box-shadow: 0 0 0 4px rgba(234, 228, 213, 0.12);
}
</style>
