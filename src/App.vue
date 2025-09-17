<template>
  <div class="relative flex flex-col min-h-screen text-gray-100 overflow-hidden">
    <!-- Fond animé et particules -->
    <div class="absolute inset-0 -z-10">
      <div
        v-for="n in 30"
        :key="n"
        class="particle"
        :style="{
          '--rand-top': Math.random(),
          '--rand-left': Math.random(),
          '--rand-speed': 5 + Math.random() * 5
        }"
      />
    </div>

    <!-- Navbar -->
    <Navbar class="relative z-20" />

    <!-- Contenu des pages -->
    <main class="flex-1 relative z-10">
      <router-view v-slot="{ Component }">
        <transition name="fade-slide" mode="out-in">
          <component :is="Component" />
        </transition>
      </router-view>
    </main>

    <!-- Footer -->
    <Footer class="relative z-20" />
  </div>
</template>

<script setup>
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'
</script>

<style>
/* Fond dégradé animé */
@keyframes gradientShift {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

body {
  background: linear-gradient(120deg, #1f2937, #111827, #374151, #111827);
  background-size: 400% 400%;
  animation: gradientShift 15s ease infinite;
  font-family: 'Inter', sans-serif;
}

/* Pattern diagonale */
body::before {
  content: "";
  position: fixed;
  inset: 0;
  background-image: repeating-linear-gradient(
    45deg,
    rgba(255,255,255,0.02),
    rgba(255,255,255,0.02) 1px,
    transparent 1px,
    transparent 10px
  );
  pointer-events: none;
  z-index: -20;
}

/* Light streaks */
body::after {
  content: "";
  position: fixed;
  inset: 0;
  background: linear-gradient(90deg, rgba(255,255,255,0.03) 0%, rgba(255,255,255,0) 100%);
  animation: streakMove 20s linear infinite;
  pointer-events: none;
  z-index: -15;
}

@keyframes streakMove {
  0% { background-position: -100% 0; }
  100% { background-position: 100% 0; }
}

/* Particules animées */
.particle {
  width: 4px;
  height: 4px;
  background: rgba(255,255,255,0.2);
  border-radius: 50%;
  position: absolute;
  top: calc(100% * var(--rand-top));
  left: calc(100% * var(--rand-left));
  animation: particleMove calc(10s * var(--rand-speed)) linear infinite;
  opacity: 0;
}

@keyframes particleMove {
  0% { transform: translate(0,0); opacity: 0; }
  50% { opacity: 1; }
  100% { transform: translate(200px, -150px); opacity: 0; }
}

/* Fade in up */
@keyframes fade-in-up {
  0% { opacity: 0; transform: translateY(20px); }
  100% { opacity: 1; transform: translateY(0); }
}
.animate-fade-in-up {
  animation: fade-in-up 1s ease forwards;
}

/* Transition pages */
.fade-slide-enter-active, 
.fade-slide-leave-active {
  transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}
.fade-slide-enter-from {
  opacity: 0;
  transform: translateY(20px);
}
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}
</style>
