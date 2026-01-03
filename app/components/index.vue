<template>
  <div class="relative min-h-screen flex items-center justify-center overflow-hidden
              bg-gradient-to-br from-pink-100 via-pink-200 to-rose-200">

    <!-- floating hearts -->
    <div v-if="showMessage">
      <span
        v-for="i in 12"
        :key="i"
        class="absolute bottom-0 text-pink-400 animate-float"
        :style="randomStyle()"
      >
        💖
      </span>
    </div>

    <!-- card -->
    <div
      class="bg-white rounded-3xl shadow-2xl p-10 text-center max-w-md w-full
             transition-all duration-700"
      :class="showMessage ? 'scale-110 rotate-1' : 'scale-100'"
    >
      <!-- new image -->
      <img
        src="https://cdn-icons-png.flaticon.com/512/742/742751.png"
        alt="love"
        class="w-32 mx-auto mb-6 drop-shadow-lg"
        :class="showMessage ? 'animate-pulse' : 'animate-bounce'"
      />

      <h1 class="text-3xl font-extrabold text-pink-500 mb-2">
        💖 Surprise! 💖
      </h1>

      <p class="text-gray-600 mb-6">
        พี่มีอะไรจะบอกหมูอ้วนนน...
      </p>

      <!-- message -->
      <div v-if="showMessage" class="space-y-3 animate-pop">
        <p class="text-2xl font-bold text-rose-500">
          รักหมูที่สุดดดดด 💕
        </p>
        <p class="text-pink-400">
          ขอบคุณที่อยู่ด้วยกันเสมอ 🌷
        </p>
      </div>

      <!-- button -->
      <button
        v-if="!showMessage"
        @click="showMessage = true"
        class="mt-6 px-8 py-3 rounded-full text-white text-lg font-semibold
               bg-gradient-to-r from-pink-400 to-rose-400
               hover:from-pink-500 hover:to-rose-500
               hover:scale-110 active:scale-95
               transition-all duration-300 shadow-lg"
      >
        กดดูเซอร์ไพรส์ 🎁
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const showMessage = ref(false)

const randomStyle = () => ({
  left: Math.random() * 100 + '%',
  animationDelay: Math.random() * 2 + 's',
  fontSize: Math.random() * 20 + 16 + 'px'
})
</script>

<style>
@keyframes float {
  0% {
    transform: translateY(0) scale(1);
    opacity: 1;
  }
  100% {
    transform: translateY(-120vh) scale(1.5);
    opacity: 0;
  }
}

.animate-float {
  animation: float 6s linear infinite;
}

@keyframes pop {
  0% {
    transform: scale(0.5);
    opacity: 0;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}

.animate-pop {
  animation: pop 0.6s ease-out forwards;
}
</style>
