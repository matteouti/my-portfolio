<template>
  <section class="max-w-6xl mx-auto py-20 px-4 relative z-10">
    <h2 class="text-4xl font-bold mb-12 text-center animate-fade-in-up">
      Services
    </h2>

    <div class="grid md:grid-cols-3 gap-8">
      <!-- Développement Backend -->
      <div class="bg-gray-800 bg-opacity-80 p-8 rounded-xl shadow-lg transform hover:-translate-y-2 hover:scale-105 transition-all text-center animate-fade-in-up" style="animation-delay: 0.1s">
        <svg xmlns="http://www.w3.org/2000/svg" class="mx-auto h-12 w-12 text-yellow-400 mb-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-3 0-6 2-6 6s3 6 6 6 6-2 6-6-3-6-6-6z" />
        </svg>
        <h3 class="text-2xl font-semibold mb-2">Développement Backend</h3>
        <p class="text-gray-300">
          Applications web robustes avec <span class="text-yellow-400 font-bold">Laravel</span>, gestion de bases MySQL/PostgreSQL et APIs sécurisées.
        </p>
      </div>

      <!-- Développement Frontend -->
      <div class="bg-gray-800 bg-opacity-80 p-8 rounded-xl shadow-lg transform hover:-translate-y-2 hover:scale-105 transition-all text-center animate-fade-in-up" style="animation-delay: 0.3s">
        <svg xmlns="http://www.w3.org/2000/svg" class="mx-auto h-12 w-12 text-yellow-400 mb-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v2a2 2 0 002 2h12a2 2 0 002-2v-2M4 12h16M4 8h16M4 4h16" />
        </svg>
        <h3 class="text-2xl font-semibold mb-2">Développement Frontend</h3>
        <p class="text-gray-300">
          Interfaces modernes et réactives avec <span class="text-yellow-400 font-bold">Vue.js</span> et <span class="text-yellow-400 font-bold">TailwindCSS</span>.
        </p>
      </div>

      <!-- Maintenance & Optimisation -->
      <div class="bg-gray-800 bg-opacity-80 p-8 rounded-xl shadow-lg transform hover:-translate-y-2 hover:scale-105 transition-all text-center animate-fade-in-up" style="animation-delay: 0.5s">
        <svg xmlns="http://www.w3.org/2000/svg" class="mx-auto h-12 w-12 text-yellow-400 mb-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
        </svg>
        <h3 class="text-2xl font-semibold mb-2">Maintenance & Optimisation</h3>
        <p class="text-gray-300">
          Mise à jour, refactoring, correction de bugs et optimisation continue pour des projets web performants.
        </p>
      </div>
    </div>
  </section>
</template>

<script setup>
// Pas de script nécessaire pour cette section
</script>

<style scoped>
/* Animation fade-in-up simple */
@keyframes fadeInUp {
  0% {
    opacity: 0;
    transform: translateY(20px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}
.animate-fade-in-up {
  animation: fadeInUp 0.8s ease forwards;
}
</style>
