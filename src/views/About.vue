<template>
  <section class="max-w-4xl mx-auto py-20 px-4 space-y-12 relative z-10">
    <!-- Titre -->
    <h2 class="text-4xl font-bold mb-6 text-center animate-fade-in-up">
      À propos de moi
    </h2>

    <!-- Présentation -->
    <div class="space-y-4 animate-fade-in-up" style="animation-delay: 0.2s">
      <p class="text-gray-300">
        Je suis un développeur web freelance spécialisé en 
        <span class="text-yellow-400 font-semibold">Laravel</span> et 
        <span class="text-yellow-400 font-semibold">Vue.js</span>.  
        J’aime créer des applications modernes, performantes et belles, avec une attention particulière à l’expérience utilisateur.
      </p>
      <p class="text-gray-300">
        Passionné par le <span class="text-yellow-400 font-semibold">live coding</span> et les outils d'<span class="text-yellow-400 font-semibold">IA pour assister le développement</span>, je cherche toujours à rendre mes projets plus rapides, fiables et innovants.
      </p>
    </div>

    <!-- Photo -->
    <div class="text-center mt-8 animate-fade-in-up" style="animation-delay: 0.4s">
      <img 
        :src="myPhoto" 
        alt="Moi" 
        class="mx-auto rounded-full shadow-lg w-48 h-48 object-cover transition-transform duration-500 transform hover:scale-110 hover:shadow-2xl"
      />
    </div>

    <!-- Compétences -->
    <div class="mt-12">
      <h3 class="text-2xl font-bold mb-4 animate-fade-in-up">Mes outils & compétences</h3>
      <div class="flex flex-wrap gap-3 justify-center animate-fade-in-up" style="animation-delay: 0.6s">
        <span class="badge">PHP</span>
        <span class="badge">Laravel</span>
        <span class="badge">Vue.js</span>
        <span class="badge">MySQL</span>
        <span class="badge">TailwindCSS</span>
        <span class="badge">Live Coding</span>
        <span class="badge">IA pour Dev</span>
      </div>
    </div>
  </section>
</template>

<script setup>
import myPhoto from "@/assets/img/my-photo.jpg";
</script>

<style scoped>
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

/* Badges dynamiques */
.badge {
  background-color: #374151;
  color: #facc15;
  padding: 0.3rem 0.8rem;
  border-radius: 9999px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
}
.badge:hover {
  background: #facc15;
  color: #1f2937;
  transform: translateY(-3px) scale(1.1);
  box-shadow: 0 4px 10px rgba(250, 204, 21, 0.5);
}
</style>
