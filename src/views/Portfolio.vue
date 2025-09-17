<template>
  <section class="max-w-6xl mx-auto py-20 px-4 relative z-10">
    <h2 class="text-4xl font-bold mb-10 text-center">Mes Projets</h2>
    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
      <div v-for="project in projects" :key="project.id" class="relative group overflow-hidden rounded-lg shadow cursor-pointer">
        <img :src="project.image" class="w-full h-48 object-cover transition-transform duration-500 group-hover:scale-110" />
        <div class="absolute inset-0 bg-black bg-opacity-60 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex flex-col justify-center items-center text-center text-white p-4">
          <h3 class="text-xl font-semibold mb-2">{{ project.title }}</h3>
          <p>{{ project.description }}</p>
          <router-link :to="project.link" class="mt-2 inline-block bg-yellow-400 text-gray-900 px-4 py-2 rounded hover:bg-yellow-500 transition">Voir le projet</router-link>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  setup() {
    const projects = [
      { id: 1, title: "Projet Alpha", description: "Site web Vue.js moderne", image: "https://placehold.co/400x300?text=Alpha", link: "#" },
      { id: 2, title: "Projet Beta", description: "Application mobile React Native", image: "https://placehold.co/400x300?text=Beta", link: "#" },
      { id: 3, title: "Projet Gamma", description: "Dashboard admin TailwindCSS", image: "https://placehold.co/400x300?text=Gamma", link: "#" },
      { id: 4, title: "Projet Delta", description: "Landing page marketing", image: "https://placehold.co/400x300?text=Delta", link: "#" },
      { id: 5, title: "Projet Epsilon", description: "Portfolio interactif", image: "https://placehold.co/400x300?text=Epsilon", link: "#" },
      { id: 6, title: "Projet Zeta", description: "Blog responsive", image: "https://placehold.co/400x300?text=Zeta", link: "#" },
    ];
    return { projects };
  }
}
</script>
