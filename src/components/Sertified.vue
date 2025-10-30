<template>
  <div class="flex flex-col items-center justify-center min-h-screen bg-pattern text-white text-center p-6 relative">
    
    <!-- Ikon animasi -->
    <div class="animate-bounce">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-24 w-24 mx-auto text-purple-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"
          d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
      </svg>
    </div>

    <!-- Judul -->
    <h1 class="text-4xl md:text-5xl font-bold mt-6 mb-4 split-f">
      Sedang Dalam Perawatan
    </h1>

    <!-- Deskripsi -->
    <p class="text-gray-300 max-w-xl mx-auto mb-8">
      Kami sedang melakukan pemeliharaan sistem untuk peningkatan layanan.
      Silakan kembali beberapa saat lagi 💜
    </p>

    <!-- Tombol -->
    <div class="mt-4 flex flex-col md:flex-row gap-4">
      <button
        @click="checkStatus"
        class="btn-accent hover:scale-105 transition-transform duration-200 shadow-lg">
        Coba Lagi
      </button>

      <a href="https://xo-chatttv2.vercel.app/chat"
         class="px-6 py-3 border border-purple-500 text-purple-400 hover:bg-purple-800 rounded-2xl transition-all duration-200 shadow-inner">
        Hubungi Kami
      </a>
    </div>
 <p class="text-gray-400 text-cente margin-top-6 mt-6">
        *NOTE : Login dahulu ke webnya, lalu add new chat di pojok kanan bawah, cari (admin@admin.com)</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const isChecking = ref(false)

function checkStatus() {
  isChecking.value = true
  setTimeout(() => {
    alert('Server masih dalam perawatan. Silakan coba lagi nanti!')
    isChecking.value = false
  }, 1500)
}
</script>

<style scoped>
/* ===== THEME COLORS & BACKGROUND ====== */
.bg-pattern {
  background-color: #0f0f10;
  background-image: 
    linear-gradient(45deg, rgba(255,255,255,0.05) 1px, transparent 1px),
    linear-gradient(-45deg, rgba(255,255,255,0.05) 1px, transparent 1px);
  background-size: 40px 40px;
}

/* ===== INPUT STYLE ====== */
.contact-input {
  width: 100%;
  background-color: rgba(168, 85, 247, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  color: #e0e0e0;
  padding: 10px 14px;
  border-radius: 12px;
  font-size: 1rem;
  outline: none;
  transition: all 0.3s ease;
}
.contact-input::placeholder {
  color: rgba(255, 255, 255, 0.5);
}
.contact-input:focus {
  border-color: #a855f7;
  box-shadow: 0 0 12px #a855f780;
}

/* ===== BUTTON STYLE ====== */
.btn-accent {
  border: 1px solid #a855f7;
  color: #a855f7;
  background: rgba(168, 85, 247, 0.1);
  border-radius: 12px;
  padding: 12px 18px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  backdrop-filter: blur(6px);
  box-shadow: 0 4px 15px rgba(168,85,247,0.3);
}
.btn-accent:hover {
  background-color: #a855f7;
  color: white;
  box-shadow: 0 6px 20px rgba(168,85,247,0.6);
}

/* ===== ALERT STYLE ====== */
.alert {
  position: fixed;
  bottom: 1.5rem;
  right: 1.5rem;
  padding: 14px 22px;
  border-radius: 14px;
  color: #fff;
  font-weight: 500;
  box-shadow: 0 4px 25px rgba(0, 0, 0, 0.3);
  backdrop-filter: blur(8px);
  transition: all 0.3s ease;
}
.alert-success {
  background-color: rgba(34, 197, 94, 0.8);
}
.alert-error {
  background-color: rgba(220, 38, 38, 0.8);
}

/* ===== FADE ANIMATION ====== */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* ===== TITLE ANIMATION ====== */
.split-f {
  display: inline-block;
  overflow: hidden;
  background: linear-gradient(90deg, #a855f7, #6b21a8);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

/* ===== BACKGROUND EFFECT ====== */
.bg-blur {
  backdrop-filter: blur(12px);
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 16px;
}
</style>
