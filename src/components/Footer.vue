<template>
  <footer>
    <div
      class="bg-primary min-h-screen px-6 py-16 flex flex-col justify-center items-center relative overflow-hidden"
      id="f-wrapper"
    >
      <Bg :hue="0" :saturation="0" :lightness="100" class="opacity-10 absolute inset-0" />

      <h1 class="text-5xl text-center text-light-gray font-semibold mb-10 split-f">
        Contact<span class="text-accent">.</span>
      </h1>

      <!-- Contact Form -->
      <form
        @submit.prevent="sendMessage"
        class="w-full max-w-md bg-secondary/20 backdrop-blur-md rounded-2xl p-8 shadow-lg border border-light-gray/20"
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
            class="mt-4 w-full border border-accent text-accent py-2 rounded-md hover:bg-accent hover:text-white transition-all duration-300 font-medium"
          >
            Send
          </button>
        </div>
      </form>

      <!-- Floating Alert -->
      <transition name="fade">
        <div
          v-if="alert.visible"
          :class="[
            'fixed bottom-6 right-6 px-5 py-3 rounded-xl text-white shadow-lg backdrop-blur-md transition-all',
            alert.type === 'success'
              ? 'bg-green-600/80'
              : 'bg-red-600/80'
          ]"
        >
          {{ alert.message }}
        </div>
      </transition>
    </div>
  </footer>

  <!-- Footer -->
    <footer class="absolute bottom-4 text-sm text-gray-500 text-center w-full">
      © {{ new Date().getFullYear() }} FizzxVerss. All rights reserved.
    </footer>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { SplitText } from 'gsap/SplitText';
import gsap from 'gsap';
import Bg from './util/Bg.vue';

// ==== KONFIG TELEGRAM ====
const BOT_TOKEN = "6439522031:AAGphEnYCdsDVZQYt-a6mMZmV0zqZ2g6RC8";
const CHAT_ID = 6450551010;

// ==== STATE ====
const name = ref('');
const email = ref('');
const message = ref('');
const alert = ref({ visible: false, message: '', type: 'success' });

// ==== ALERT ====
function showAlert(msg, type = 'success') {
  alert.value = { visible: true, message: msg, type };
  setTimeout(() => (alert.value.visible = false), 3000);
}

// ==== KIRIM KE TELEGRAM ====
const sendMessage = async () => {
  if (!name.value.trim() || !email.value.trim() || !message.value.trim()) return;

  const text = `📩 *Pesan Baru dari Website Portfolio*\n\n👤 Nama: ${name.value}\n📧 Email: ${email.value}\n💬 Pesan:\n${message.value}`;
  try {
    const res = await fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        chat_id: CHAT_ID,
        text,
        parse_mode: 'Markdown'
      })
    });

    if (res.ok) {
      showAlert('Pesan berhasil dikirim ke Telegram 🚀', 'success');
      name.value = '';
      email.value = '';
      message.value = '';
    } else {
      throw new Error('Gagal mengirim');
    }
  } catch {
    showAlert('Gagal mengirim pesan. Coba lagi nanti.', 'error');
  }
};

// ==== ANIMASI GSAP ====
onMounted(() => {
  const split = SplitText.create('.split-f', {
    type: 'words',
    mask: 'words'
  });

  gsap.from(split.words, {
    scrollTrigger: {
      trigger: '#f-wrapper',
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
  color: #a855f7; /* ungu neon */
}
.contact-input {
  width: 100%;
  background-color: rgba(168, 85, 247, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  color: #e0e0e0;
  padding: 10px 14px;
  border-radius: 8px;
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

/* Fade animation for alert */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
