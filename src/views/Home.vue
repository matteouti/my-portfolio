<template>
  <section class="relative flex flex-col items-center justify-center min-h-screen px-4 text-center z-10 overflow-hidden">
    <!-- Badges flottants orbitaux -->
    <div class="absolute inset-0 flex items-center justify-center pointer-events-none">
      <span
        v-for="(skill, i) in orbitSkills"
        :key="i"
        class="absolute bg-yellow-400 text-gray-900 px-3 py-1 rounded-full text-sm md:text-base shadow-lg animate-orbit hover:scale-110 transition-all"
        :style="{
          transform: `rotate(${i * 72}deg) translateX(180px) rotate(-${i * 72}deg)`,
          animationDelay: `${i * 0.4}s`
        }"
      >
        {{ skill }}
      </span>
    </div>

    <!-- Nom avec glow -->
    <h1 class="text-5xl md:text-6xl font-bold mb-4 animate-fade-in-up text-white drop-shadow-lg glow-text max-w-full break-words">
      Randriamanjato  Mattéouti 
    </h1>

    <!-- Typing effect -->
    <p class="text-xl md:text-2xl text-yellow-400 mb-6 animate-fade-in-up" style="animation-delay: 0.2s">
      <span ref="typingText"></span>
    </p>

    <!-- Bouton voir projets -->
    <router-link
      to="/portfolio"
      class="bg-yellow-400 text-gray-900 px-6 py-3 rounded-lg hover:bg-yellow-500 transform hover:scale-110 transition-all animate-fade-in-up shadow-lg glow-btn max-w-max mx-auto"
      style="animation-delay: 0.6s"
    >
      Voir mes projets
    </router-link>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const orbitSkills = ["PHP", "Laravel", "Vue.js", "IA", "UI/UX"];

const typingText = ref(null);
const phrases = ["Développeur Fullstack PHP & VueJS", "Passionné de Live Coding", "Code assisté par IA"];
let index = 0;
let charIndex = 0;

const type = () => {
  if (!typingText.value) return;
  if (charIndex < phrases[index].length) {
    typingText.value.textContent += phrases[index][charIndex];
    charIndex++;
    setTimeout(type, 100);
  } else {
    setTimeout(() => {
      typingText.value.textContent = "";
      charIndex = 0;
      index = (index + 1) % phrases.length;
      type();
    }, 2000);
  }
};

onMounted(() => type());
</script>

<style scoped>
/* Fade-in-up */
.animate-fade-in-up {
  animation: fade-in-up 1s ease forwards;
}
@keyframes fade-in-up {
  0% { opacity: 0; transform: translateY(20px); }
  100% { opacity: 1; transform: translateY(0); }
}

/* Glow text */
.glow-text {
  text-shadow: 0 0 10px #facc15, 0 0 20px #fcd34d, 0 0 30px #fbbf24;
}

/* Glow bouton */
.glow-btn {
  box-shadow: 0 0 8px #facc15, 0 0 16px #fcd34d, 0 0 24px #fbbf24;
}

/* Badges orbitaux */
@keyframes orbit {
  0% { transform: rotate(0deg) translateX(180px) rotate(0deg); }
  100% { transform: rotate(360deg) translateX(180px) rotate(-360deg); }
}
.animate-orbit {
  animation: orbit 12s linear infinite;
}

/* Hover scaling pour badges */
.animate-orbit:hover {
  transform: scale(1.2);
  transition: transform 0.3s;
}
</style>
